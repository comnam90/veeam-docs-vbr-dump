---
title: "Archiving Job"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/archiving_job.html"
last_updated: "4/29/2025"
product_version: "13.0.1.1071"
---

# Archiving Job

In this article

The process of moving backup data from the performance or capacity tier to the archive tier is called an archiving job. This job runs in a separate session and follows the default schedule of the offload job (this job moves data from the performance tier to the capacity tier).

During the archiving job, new backup data is offloaded to the archive tier, while the outdated backup data is cleaned up from the archive tier during the same archiving session. To clean up outdated data, a cleanup task runs in parallel with the archiving job. After the archiving job finishes, the moved data is deleted from the performance tier. For the capacity tier, it happens during the next offload job.

How Archiving Job Works

The archiving job works according to the following algorithm:

1. Veeam Backup & Replication gets metadata information about blobs and data blocks that should be archived.
2. If any blocks are available in the archive tier, Veeam Backup & Replication adds them to the archiving job. The archiving job will re-use these blocks within the archiving session.
3. Veeam Backup & Replication gets a list of all blocks that should be archived.
4. Veeam Backup & Replication arranges the blocks from the list into sets. The identical blocks from different tiers are arranged into one set.
5. From each set of identical blocks, Veeam Backup & Replication selects one block that will be archived. If the set contains a block not present in the archived tier, Veeam Backup & Replication adds this block to the blob.

|  |
| --- |
| Note |
| Consider the following:   * This option depends on whether the data block reuse is enabled. By default, Veeam Backup & Replication enables the data block reuse when you configure the archive tier. To disable this option, [modify the settings of your archive tier](new_archive_tier.md#reuse). * The archiving tier inherits encrypted data from the capacity tier. The blocks encrypted on the capacity level are moved to the archive tier in the encrypted state. |

1. Veeam Backup & Replication arranges blocks into blobs according to the [blob optimization algorithm](#blobs).
2. Veeam Backup & Replication generates metadata for blobs that will be archived. This metadata is used to identify the location of each block in the blob.
3. Veeam Backup & Replication uploads blobs with blocks that are not present in the archive tier.
4. Veeam Backup & Replication uploads metadata to the archive tier.

Blob Optimization

Blob optimization helps organize data efficiently and reduces the storage space required on the archive tier. During the archiving job, Veeam Backup & Replication modifies the blocks of data from the performance/capacity tier and rearranges these data into blobs. The size of these blobs differs from the size of blocks of data on the performance/capacity tier and depends on the [storage optimization option](compression_deduplication.md#optimization) of a backup job.

To arrange blocks into blobs, the archiving job analyzes the size of data blocks in the performance/capacity tier. It does not decompress data blocks, but uses already compressed data and arranges them into a blob according to the following rules:

* The blob must not contain more than 512 data blocks.
* The blob must not occupy more than 512 MB.

Depending on the storage optimization option, the size of a blob in the archive tier can be calculated the following way:

* If the storage optimization option is set to 1 or 4 MB, the archiving job rearranges data blocks into a single blob that occupies no more than 512 MB.
* If the storage optimization option is set to 512 KB, the archiving job rearranges data blocks into a single blob that occupies no more than 256 MB.
* If the storage optimization option is set to 256 KB, the archiving job rearranges data blocks into a single blob that occupies no more than 128 MB.

For example, due to the storage optimization option of a backup job, each data block located on the performance/capacity tier occupies no more than 1 MB. During the archiving job session, the job checks the block size and recompiles it into larger blobs. Thus, the total amount of blocks in a blob will be 512, and this blob will occupy no more than 512 MB.

Considerations and Limitations

You can archive backups if they meet the following conditions:

* The type of a backup file is supported. For details, see [Archive Tier](archive_tier.md#types).
* Backup files belong to inactive backup chains.
* Backup files have been created N days ago according to Archive backup files older than N days setting of the [Add Archive Tier](new_archive_tier.md) step of the wizard.
* If you have selected the Archive backups only if the remaining retention time is above minimal storage period check box of the [Add Archive Tier](new_archive_tier.md) step of the wizard:

1. [For Amazon S3 Glacier storage] Only backup files with retention period no less than 90 days.
2. [For Microsoft Azure Archive storage] Only backup files with retention period no less than 180 days.

Backup files that meet all the following conditions will be cleaned up:

* Backup files that do not have original files on the performance tier.
* Backup files with the expired or unspecified immutability period. For more information, see [Immutability for Archive Tier](immutability_archive_tier.md).

Page updated 4/29/2025

Page content applies to build 13.0.1.1071
