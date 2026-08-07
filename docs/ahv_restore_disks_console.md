---
title: "Disk Restore Using Console"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_restore_disks_console.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Disk Restore Using Console


In case a disaster strikes, you can restore disks of a Nutanix AHV VM from a backup or backup snapshot. Veeam Backup & Replication allows you to attach the restored disks to the original VM or any other VM in the virtual infrastructure.

|  |
| --- |
| Note |
| You cannot restore disks of volume groups attached to the VM. |

To restore disks attached to a protected VM using Veeam Backup & Replication console, do the following:

1. [Launch the Virtual Disk Restore wizard](ahv_restore_disks_launch.md).
2. [Select a VM](ahv_restore_disks_select_disks.md).
3. [Select a restore point](ahv_restore_disks_restore_point.md).
4. [Configure mapping settings](ahv_restore_disks_mapping.md).
5. [Specify a reason for the restore](ahv_restore_disks_reason.md).
6. [Finish working with the wizard](ahv_restore_disks_summary.md).

Page updated 2026-05-19

