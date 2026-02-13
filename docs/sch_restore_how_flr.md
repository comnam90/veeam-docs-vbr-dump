---
title: "File-Level Recovery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/sch_restore_how_flr.html"
last_updated: "10/27/2025"
product_version: "13.0.1.1071"
---

# File-Level Recovery


To recover VM files and folders from a backup, Veeam Plug-in for Scale Computing HyperCore performs the following steps:

1. Mounts disks of the backed-up VM to either of the following instances:

* To the backup server or a [mount server](guest_file_recovery.md) — if the VM guest OS is Microsoft Windows.
* To the helper host — if the VM guest OS is a Linux-based operating system.

1. Launches the Veeam Backup Browser.

The Veeam Backup Browser displays the directory structure of the backed-up VM. In the browser, you select the necessary files and folders to restore.

1. Restores the selected files and folders to the original location or to a new location.
2. Detaches the disks from the backup server, mount server or helper host.

To learn how to recover individual VM files and folders, see [Performing File-Level Restore](sch_vm_guest_restore.md).


