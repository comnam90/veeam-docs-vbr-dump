---
title: "Removing Backups from Capacity or Archive Tier"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/object_storage_removing_data.html"
last_updated: "8/4/2025"
product_version: "13.0.1.1071"
---

# Removing Backups from Capacity or Archive Tier


To remove moved or copied backups from capacity or archive extent, use the Delete from disk feature, as described in section [Deleting Backups from Scale-Out Backup Repositories](deleting_backups_from_sobr.md).

Consider the following:

* When removing offloaded backup files from the backup chain that was created with the per-machine method, the associated blocks of data will be removed from the capacity or archive extent altogether.

For more information about per-machine backups, see [Backup Chain Formats](per_vm_backup_files.md).

* When removing offloaded backup files from the backup chain that was created as a single-file backup file, then nothing will be removed until either of the following occurs:

+ All the VMs were removed from the backup.
+ The backup itself was removed.

* Immutable backups cannot be removed.

For more information, see [Immutability for Scale-Out Backup Repositories](immutability_sobr.md).

* If the capacity or archive extent has been put into the Maintenance mode, the removal of data from such a repository is not possible until the extent is removed from the Maintenance mode.

For more information, see [Switching to Maintenance Mode](sobr_maintenance.md).

* During data removal, the entire folder structure starting from the repository folder (<backup\_id>) will be completely purged.

For more information on how Veeam Backup & Replication stores data in the capacity extent, see [Capacity Extent Structure](object_storage_repository_structure.md).

* If backup files with metadata that are located on your extents have been removed locally in any way other than by using the [Deleting from Disk](delete_backup_from_disk.md) feature, Veeam Backup & Replication will not be able to synchronize the backup chain state with that of the capacity or archive extent. Therefore, the offloaded blocks of data will continue to remain in cloud storage. To remove such blocks, use your cloud platform abilities.

Related Topics

* [Moving Backups to Capacity Tier](capacity_tier_move.md)
* [Copying Backups to Capacity Tier](capacity_tier_copy.md)


