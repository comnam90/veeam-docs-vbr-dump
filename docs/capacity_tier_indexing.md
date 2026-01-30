---
title: "Indexes"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/capacity_tier_indexing.html"
last_updated: "10/18/2024"
product_version: "13.0.1.1071"
---

# Indexes


|  |
| --- |
| Important |
| Starting from Veeam Backup & Replication 12, indexes are no longer used. Indexes will be removed after the first offload session once you upgrade to Veeam Backup & Replication version 12. |

To reduce the number of cost-based operations incurred by your cloud storage provider and to decrease the amount of traffic being sent over the network when moving or copying data to object storage, Veeam Backup & Replication uses indexes.

Index behavior has the following peculiarities:

* Indexes are created (or updated) during each offload or copy session and consist of hash values of blocks that are being transferred to the capacity tier. These hashes are retrieved from meta information of your backup files (VBK, VIB, or VRB).

* Indexes are stored in the ArchiveIndex directory that is located on the Performance Tier.

On each subsequent offload/copy session, Veeam Backup & Replication reuses these indexes to verify whether new blocks that are about to be transferred to the capacity tier have not been offloaded earlier. Verification is done by comparing existing indexes hashes with that of a block being transferred.

* If backups are created using the [per-machine method](per_vm_backup_files.md), indexes are built per backup chain and cannot have any cross references to any other backup chains. If all VM data is backed up to a single storage, indexes are built for the whole backup.

* Indexes are updated every time a backup chain is modified.

For example, some data may have been removed due to the retention policy threshold, or you may have removed it manually. Both scenarios will modify your indexes upon the next successful offload or copy session to maintain consistency.

* Corrupted indexes can be rebuilt by using the Rescan feature, as described in section [Rescanning Scale-Out Repositories](sobr_rescan.md).

Once an index is rebuilt, Veeam Backup & Replication will have to wait for 24 hours before it can offload any data again. This is necessary to comply with the eventual consistency model of S3 compatible object storage repositories.

ArchiveIndex Directory Structure

When Veeam Backup & Replication creates indexes, it also creates and maintains the following directory structure on each extent.

![Indexes](images/indexes_structure.webp)

| Directory | Description |
| --- | --- |
| ArchiveIndex | The root directory for keeping indexes. |
| <backup\_id> | Contains objects in a backup file. |
| <objects\_in\_backup\_id> | An identifier of an object in a backup file.   * If a backup was created using the per-machine method, then each VM will be placed to its own directory.  * If a backup was created as a single-file backup, then all the VMs will be placed to a unique directory. |
| stg\_index | Contains indexes of offloaded backup files (VBK, VIB, or VRB). |
| index\_data.vbk | Contains meta information on hash values stored in index files. |

Related Topics

* [Data Transfer](capacity_tier_data_transfer.md)

* [Backup Chain Detection](capacity_tier_inactive_backup_chain.md)
* [Retention Policy](capacity_tier_retention.md)
* [Removing Backups from Capacity or Archive Tier](object_storage_removing_data.md)


