---
title: "Restoring Volumes"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/integration_volume_restore.html"
last_updated: "2/20/2026"
product_version: "13.0.1.1071"
---

# Restoring Volumes


If data on a computer volume gets corrupted or lost, you can use Veeam Backup & Replication to restore such computer volume or all volumes from a backup created with Veeam Agent for Microsoft Windows.

When you perform volume restore, Veeam Backup & Replication restores the entire contents of the volume. It retrieves from the backup data blocks pertaining to a specific volume and copies them to the necessary location. Keep in mind that you cannot browse the volume in the backup and select individual application items, files and folders for restore. For granular file-level restore, you can use the [restore guest files](integration_flr.md) option.

A volume can be restored to the original volume or another volume. If you restore the volume to its original location, Veeam Backup & Replication overwrites data on the original volume. If you restore the volume to a another volume, and the target disk contains data, Veeam Backup & Replication overwrites the data on the target volume with data from the backup.

A volume can be restored to another volume that has greater or less space than the size of the volume in the backup. Depending on the amount of free disk space on the target volume, you can select either to shrink or to extend the volume during restore.

Before you perform volume restore, [check prerequisites](integration_volume_restore_before.md). Then use the Volume Restore wizard to restore the necessary volumes.

1. [Launch the Volume Level Restore wizard](integration_volume_restore_launch.md).
2. [Select a backup](integration_volume_restore_backup.md).
3. [Select a restore point](integration_volume_restore_point.md).
4. [Map restored disks](integration_volume_restore_disk_mapping.md).
5. [Resize restored volumes](integration_volume_restore_resize.md).
6. [Specify secure restore settings](integration_volume_restore_secure.md).
7. [Specify restore reason](integration_volume_restore_reason.md).
8. [Complete the restore process](integration_volume_restore_complete.md).


