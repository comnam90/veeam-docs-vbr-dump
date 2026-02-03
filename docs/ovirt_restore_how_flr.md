---
title: "File-Level Recovery"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ovirt_restore_how_flr.html"
last_updated: "1/27/2026"
product_version: "13.0.1.1071"
---

# File-Level Recovery


To restore VM files and folders, Veeam Plug-in for oVirt KVM performs the following steps:

1. [Applies only if you perform restore of files and folders from a VM with an operation system other than Microsoft Windows] Launches a helper host.

A helper host is a VM running the Linux operating system with a minimal set of components.

1. Mounts disks of the VM to either of the following instances:

* To the backup server or a [mount server](mount_server.md) — if the VM guest OS is Microsoft Windows.
* To the helper host — if the VM guest OS is a Linux-based operating system.

1. Launches the Veeam Backup browser.

The Veeam Backup browser displays the file system tree of the backed-up VM. In the browser, you select the necessary files and folders to restore.

1. Restores the selected files and folders to the original location or to a new location.
2. Detaches the disks from the backup server, mount server or helper host.
3. [Applies only if you perform restore of a VM with an operation system other than Microsoft Windows] Suspends the helper host.

To learn how to restore VM files and folders, see [Performing File-Level Recovery](ovirt_vm_guest_restore.md).


