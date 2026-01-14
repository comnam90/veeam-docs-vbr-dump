---
title: "Traffic Settings"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/replica_advanced_traffic_vm.html"
last_updated: "1/22/2025"
product_version: "13.0.1.1071"
---

# Traffic Settings

In this article

You can optimize data traffic sent over network by specifying which data you want to replicate, data compression level and optimize the job performance and storage usage:

1. At the Job Settings step of the wizard, click Advanced.
2. In the Advanced Settings window, check that the Traffic tab is selected.
3. [For Microsoft Windows NTFS] By default, Veeam Backup & Replication excludes data blocks of the hiberfil.sys and pagefile.sys system files from replicas. For more information on how Veeam Backup & Replication excludes data blocks of these system files, see [Swap Files](swap_files.md).

If you want to include data blocks of the hiberfil.sys and pagefile.sys system files into replicas, clear the Exclude swap file blocks check box. Note that including these files into replicas will increase their size.

1. [[For replication from production storage](replica_data_source_vm.md)] By default, Veeam Backup & Replication does not copy deleted file blocks ("dirty" blocks on the VM guest OS) to the target location. For more information, see [Deleted File Blocks](dirty_blocks.md).

If you want to include dirty data blocks into VM replicas, clear the Exclude deleted file blocks check box. Note that including these files into replicas will increase their size.

1. From the Compression level list, select a compression level for VM replicas. For more information on data compression and compressions levels, see [Data Compression and Deduplication](compression_deduplication.md).

|  |
| --- |
| Note |
| Compression is applicable only if VM data is transferred between two backup proxies. If one backup proxy acts as the source and target backup proxy, VM data is not compressed at all. |

1. [[For replication from production storage](replica_data_source_vm.md)] In the Storage optimization section, select block size that will be used to process VMs. For more information on the data blocks sizes and how they affect performance, see [Storage Optimization](compression_deduplication.md#optimization).

![Traffic Settings](images/vm_replica_job_settings_traffic.webp)

Page updated 1/22/2025

Page content applies to build 13.0.1.1071
