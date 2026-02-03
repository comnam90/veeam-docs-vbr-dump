---
title: "File-Level Recovery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_restore_how_flr.html"
last_updated: "2/2/2026"
product_version: "13.0.1.1071"
---

# File-Level Recovery


To recover VM files and folders from a backup, Veeam Backup & Replication performs the following steps:

1. Mounts disks of the backed-up VM to the [mount server](guest_file_recovery.md) specified for the recovery operation.
2. Launches the Veeam Backup Browser.

The Veeam Backup Browser displays the file system tree of the backed-up VM. In the browser, you select the necessary files and folders to restore.

1. Restores the selected files and folders to the original location or to a new location.
2. Detaches the disks from the mount server.

To recover VM files and folders from a backup snapshot, snapshot or PD snapshot, Veeam Backup & Replication performs the following steps:

1. Deploys a [helper appliance](guest_file_recovery.md) in the Nutanix AHV cluster.
2. [Applies only if you perform restore from a snapshot or PD snapshot] Creates a temporary VM in the Nutanix AHV cluster.
3. Creates a volume group using disks of the original VM (for a backup snapshot) or of the temporary VM (for a snapshot or PD snapshot).
4. Attaches the volume group to the helper appliance.
5. [Applies only if you perform restore from a snapshot or PD snapshot] Deletes the temporary VM.
6. Launches the Veeam Backup Browser.

The Veeam Backup Browser displays the file system tree of the backed-up VM. In the browser, you select the necessary files and folders to restore.

1. Restores the selected files and folders to the original location or to a new location.
2. Detaches the volume group from the helper appliance.
3. Deletes the volume group and removes the helper appliance.

To learn how to recover individual VM files and folders, see [Performing File-Level Restore](ahv_restoring_guest_os_files.md).


