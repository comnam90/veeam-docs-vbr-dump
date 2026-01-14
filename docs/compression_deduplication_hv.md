---
title: "Data Compression and Deduplication"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/compression_deduplication_hv.html"
last_updated: "11/25/2025"
product_version: "13.0.1.1071"
---

# Data Compression and Deduplication

In this article

Veeam Backup & Replication provides mechanisms of data compression and deduplication. Data compression and deduplication let you decrease traffic going over the network and disk space required to store backup files and VM replica files.

Data Compression

Data compression decreases the size of created files but affects the duration of the backup or replication procedure. Veeam Backup & Replication allows you to select one of the following compression levels:

| Compression Level | Compression Algorithm | Description |
| --- | --- | --- |
| None | No compression | This compression level is recommended if you plan to store backup files and VM replica files on storage devices supporting hardware compression and deduplication. Disabled compression can reduce performance due to the increased amount of data to be transferred. |
| Dedupe-friendly | Rle | This compression level is recommended for some deduplicating storage appliances and when external WAN accelerators are used. |
| Optimal | Lz4 | This compression level is the recommended compression level. It provides the best ratio between compression and performance, the lowest backup proxy CPU usage and the fastest restore. |
| High | Zstd 3 | This compression level provides up to 60% of additional data reduction over the Optimal compression level at the cost of 2x higher CPU usage and 2x slower restore. |
| Extreme | Zstd 9 | This compression level provides up to 33% of additional data reduction over the High compression level at the cost of 5x higher CPU usage. |

|  |
| --- |
| Note |
| Consider the following:   * [For backup copy job] Auto is the recommended compression level for backup copy jobs. Select this level to use the compression settings of the copied backup files. * If encryption is enabled for a job and the Decompress backup data blocks before storing check box is selected in the settings of the target backup repository, Veeam Backup & Replication does not compress VM data. Therefore, in the job statistics, you may observe a higher amount of transferred data (the Transferred counter) as compared to a job for which encryption is disabled. For more information on job statistics, see [Viewing Real-Time Statistics](realtime_statistics_hv.md). * In the backup properties created with encryption, you may also see that the backup size (the Backup Size column) is larger than the original VM size (the Original Size column). For more information on backup properties, see [Viewing Backup Properties](view_backup_properties_hv.md). |

The decreased size of created files is not guaranteed, as the effectiveness of compression and deduplication depends on various factors, such as the type of source data and the target file system.

Changing Data Compression Settings

You can [change data compression settings](backup_job_advanced_storage_hv.md) for existing jobs. After you change the settings, you will not need to create new full backups to use the new settings. Veeam Backup & Replication will automatically apply the new compression level to the newly created backup files after you save the settings. Previously created backup files will not be affected.

However, if you use the [reverse incremental backup method (deprecated)](reversed_incremental_backup_hv.md), the newly created backup files will contain a mixture of data blocks compressed at different levels. For example, you have a backup job that uses the reverse incremental backup method and the Optimal level of compression. After several job sessions, you change the compression level to High. In the reverse incremental backup chains, the full backup file is rebuilt with every job session to include new data blocks. As a result, the full backup file will contain a mixture of data blocks: data blocks compressed at the Optimal level and data blocks compressed at the High level. The same behavior applies to synthetic full backups: synthetic full backups created after the compression level change will contain a mixture of data blocks compressed at different levels.

If you want the newly created backup file to contain data blocks compressed at one level, you can create an active full backup. Veeam Backup & Replication will retrieve data for the whole VM image from the production infrastructure and compress it at the new compression level. All subsequent backup files in the backup chain will also use the new compression level.

Deduplication

Data deduplication decreases the size of files. With data deduplication enabled, Veeam Backup & Replication does not store the resulting file identical data blocks and space that have been pre-allocated but not used.

We recommend enabling data deduplication for your backup jobs if they contain several VMs with a lot of free space on their logical disks or VMs with similar data blocks — for example, VMs created from the same template. Data deduplication optimizes storage usage within each individual backup job. However, note that it may decrease job performance.

Veeam Backup & Replication uses [Veeam Data Movers](veeam_transport_service.md) to deduplicate VM data:

* Veeam Data Mover in the source side deduplicates VM data at the level of VM disks. Before the source-side Veeam Data Mover starts processing a VM disk, it obtains digests for the previous restore point in the backup chain from Veeam Data Mover in the target side. The source-side Veeam Data Mover consolidates this information with CBT information from the hypervisor and filters VM disk data based on it. If some data block exists in the previous restore point for this VM, the source-side Veeam Data Mover does not transport this data block to the target. In addition, in the case of dynamically expanded disks, the source-side Veeam Data Mover skips unallocated space.
* Veeam Data Mover in the target side deduplicates VM data at the level of the backup file. It processes data for all VM disks of all VMs in the job. The target-side Veeam Data Mover uses digests to detect identical data blocks in transported data and stores only unique data blocks in the resulting backup file.

You can [change data deduplication settings](backup_job_advanced_storage_hv.md) for existing jobs. After you change the settings, you will not need to create new full backups to enable or disable the deduplication. Veeam Backup & Replication will automatically apply the change to the newly created backup files after you save the settings. Previously created backup files will not be affected.

Storage Optimization

To optimize job performance and storage usage, Veeam Backup & Replication allows you to choose the minimum data block size to process VMs. The optimal data block size depends on the type of storage you select as a target and the size of your files.

When selecting the data block size, consider the following aspects:

* When reading the VM image, Veeam Backup & Replication "splits" the VM image into blocks of the selected size. The more data blocks there are, the more time is required to process the VM image.
* [For replication and VMware Cloud Director replication] Veeam Backup & Replication writes information about every data block to the VM replica metadata stored in the backup repository. The more data blocks there are, the more metadata is written to the backup repository.
* [For changed block tracking enabled] During incremental job runs, Veeam Backup & Replication uses CBT to define changed data blocks in the VM. The larger the size of the found changed data block, the greater the amount of data transferred to the target site.

The incorrectly chosen data block size may decrease the performance. For example, when you deduplicate a large backup file to small data blocks, Veeam Backup & Replication produces a very large deduplication metadata table, which can potentially overgrow the memory and CPU resources of your backup repository. For large backup files, it is better to use large data blocks.

Veeam Backup & Replication provides several storage optimization options with different block sizes used. The following table will help you to choose the optimal option according to the size of your backup files and the storage type.

| Storage optimization option | Description |
| --- | --- |
| 4 MB (former Local target (large blocks)) | Recommended for backup files that are larger than 16 TB. This option is also recommended for HPE StoreOnce and Dell Data Domain deduplicating appliances.  This option provides the lowest deduplication ratio and the largest size of incremental files. |
| 1 MB (former Local target) | Recommended for backup and replication to SAN, DAS or local storage.  This option provides the fastest job performance but reduces the deduplication ratio because, with larger data blocks, it is less likely to find identical blocks. |
| 512 KB (former LAN target) | Recommended for backup and replication to NAS, and on-site backup and replication.  This option provides a better deduplication ratio and reduces the size of a backup file because of reduced data block sizes. |
| 256 KB (former WAN target) | Recommended if you are planning to use WAN for off-site backup and replication.  This option provides the maximum deduplication ratio and the smallest size of backup files that allow you to reduce the amount of traffic over WAN. However, note that various factors can affect the overall size of the backup files. As a result, the smallest file size may not always be achieved. |

Changing Storage Optimization Settings

You can [change storage optimization settings](backup_job_advanced_storage_hv.md) for existing jobs. New settings will not have any effect on previously created files in the chain. They will be applied to new files created after the settings were changed.

For Veeam Backup & Replication to apply the new settings, use the following instructions.

Backup Jobs

To apply new storage optimization settings in backup jobs, you must create an active full backup after you change storage optimization settings. Veeam Backup & Replication will use the new block size for the active full backup and subsequent backup files in the backup chain.

Backup Copy Jobs

To change data block size for backup copy jobs, you must perform the following actions:

1. Change the data block size in the initial backup job settings.
2. Create an active full backup with the initial backup job.
3. Create an active full backup with the backup copy job.

Page updated 11/25/2025

Page content applies to build 13.0.1.1071
