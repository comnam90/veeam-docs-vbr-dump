---
title: "File-Level Recovery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/pve_restore_how_flr.html"
last_updated: "2/2/2026"
product_version: "13.0.1.1071"
---

# File-Level Recovery


To recover VM files and folders from a backup, Veeam Backup & Replication performs the following steps:

1. Mounts disks of the backed-up VM to the [mount server](guest_file_recovery.md) specified for the recovery operation.
2. Launches the Veeam Backup Browser.

The Veeam Backup Browser displays the directory structure of the backed-up VM. In the browser, you select the necessary files and folders to restore.

1. Restores the selected files and folders to the original location or to a new location.
2. Detaches the disks from the mount server.

To learn how to recover individual VM files and folders, see [Performing File-Level Restore](pve_vm_guest_restore.md).


