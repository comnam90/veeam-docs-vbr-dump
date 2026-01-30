---
title: "Restore from Other File Systems"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/guest_restore_other.html"
last_updated: "11/19/2025"
product_version: "13.0.1.1071"
---

# Restore from Other File Systems


To recover files from OSes not supported for guest OS file restore, you can use other types of restores. For the list of file systems supported for guest OS file restore, see the [Guest OS File Restore](platform_support.md#flr) section.

Recovering Files for VMware vSphere VMs

To restore files and folders, do the following:

1. In the virtual infrastructure, find a VM that can read the file system of the original VM.
2. Use [Instant Disk Recovery](instant_disk_recovery.md) to mount a disk of the original VM to the VM that can read the file system.
3. Open the VM console and bring the disk online.
4. Copy the required files.
5. If you no longer need the disk, [stop publishing](instant_disk_recovery_finalize.md#remove) it.

Alternatively, you can mount the VM disks to a Microsoft Windows VM and use file management tools.

Recovering Files for Microsoft Hyper-V VMs

To restore files and folders, do the following:

1. Use [Instant Recovery to Microsoft Hyper-V](instant_recovery_to_hv.md) to publish the VM from the backup file on the Microsoft Hyper-V host in the virtual infrastructure. Do not start the recovered VM.
2. Mount the disks of the restored VM to any VM that can read the file system of the original VM.
3. Restore files or folders using native file management tools.

Alternatively, you can mount the VM disks to a Microsoft Windows VM and use file management tools.


