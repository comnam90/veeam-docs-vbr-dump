---
title: "Global Data Deduplication"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/wan_acceleration_sources.html"
last_updated: "5/29/2024"
product_version: "13.0.1.1071"
---

# Global Data Deduplication

In this article

The goal of WAN acceleration is to send less data over the network. To reduce the amount of data going over WAN, Veeam Backup & Replication uses the global data deduplication mechanism.

1. When you first run a job to the remote location, Veeam Backup & Replication analyzes data blocks going over WAN.
2. With every new cycle of a job to the remote location, Veeam Backup & Replication uses the data redundancy algorithm to find duplicate data blocks in copied files. Veeam Backup & Replication analyzes data blocks in files on the source side and compares them with those that have been previously transferred over WAN. If an identical data block is found, Veeam Backup & Replication deduplicates it.

As a result, only unique data blocks go over WAN. Data blocks that have already been sent are not sent. This way, Veeam Backup & Replication eliminates transfer of redundant data over WAN.

Veeam Backup & Replication uses three sources for data deduplication:

* VM disks. Veeam Backup & Replication analyses data blocks within the same VM disk. If identical blocks are found, duplicates are eliminated.
* Previous restore points for the processed VM on the target repository. Veeam Backup & Replication analyses data in the restore point that is about to be copied and the restore points that are already stored on the target side. If an identical block is found on the target side, Veeam Backup & Replication eliminates the redundant data block in the copied restore point.
* Global cache. Veeam Backup & Replication creates a global cache holding data blocks that repeatedly go over WAN. In a new job session, Veeam Backup & Replication analyzes data blocks to be sent and compares them with data blocks stored in the global cache. If an identical data block is already available in the global cache, its duplicate on the source side is eliminated and not sent over WAN.

|  |
| --- |
| Note |
| Consider the following:   * Veeam Backup & Replication deduplicates data blocks within one VM disk and in restore points for one VM only. Deduplication between VM disks and restore points of different VMs is performed indirectly, using the global cache. For more information, see [WAN Global Cache](wan_global_cache.md). * Global data deduplication and deduplication within the same VM disk are not used if both WAN accelerators in the pair (the source one and the target one) operate in the High bandwidth mode. |

Page updated 5/29/2024

Page content applies to build 13.0.1.1071
