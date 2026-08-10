---
title: "Performing Disk Restore"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/azure_performing_disk_restore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Performing Disk Restore


In case a disaster strikes, you can restore corrupted virtual disks of an Azure VM from a cloud-native snapshot or image-level backup. Veeam Plug-in for Microsoft Azure allows you to restore virtual disks to the original location or to a new location.

Before You Begin

To restore a virtual disk from a backup that is stored in an archive repository, you must retrieve the archived data first. You can either retrieve the archived data manually before you begin the restore operation, or launch the data retrieval process right from the restore wizard. To learn how to retrieve data manually, see [Retrieving Data From Archive](azure_retrieving_vm_data.md).

How to Perform Disk Restore

To restore virtual disks attached to a protected Azure VMs, do the following:

1. [Launch the Restore Disks wizard](azure_disk_restore_wizard.md).
2. [Select a restore point](azure_disk_restore_point.md).
3. [Select a service account](azure_disk_restore_account.md).
4. [Choose a restore mode](azure_disk_restore_mode.md).
5. [Specify data retrieval settings](azure_disk_retrieve.md).
6. [Specify disk settings](azure_disk_restore_disks.md).
7. [Specify a restore reason](azure_disk_restore_reason.md).
8. [Finish working with the wizard](azure_disk_restore_finish.md).

Page updated 2026-07-01

