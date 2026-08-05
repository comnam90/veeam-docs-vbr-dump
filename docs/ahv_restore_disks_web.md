---
title: "Disk Restore Using Web UI"
product: "vbr"
doc_type: "userguide"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/ahv_restore_disks_web.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Disk Restore Using Web UI


In case a disaster strikes, you can restore disks of a Nutanix AHV VM from a backup or backup snapshot. In the [Veeam Backup & Replication web UI](web_ui_logon.md), you can attach the restored disks to the original VM or any other VM in the virtual infrastructure.

|  |
| --- |
| Note |
| You cannot restore disks of volume groups attached to the VM. |

To restore disks attached to a protected VM using Web UI, do the following:

1. [Launch the Virtual Disk Restore wizard](ahv_restore_disks_launch.md).

1. [Select a restore point](ahv_restore_disks_restore_point.md).

1. [Configure mapping settings](ahv_restore_disks_mapping.md).

1. [Specify a restore reason](ahv_restore_disks_reason.md).

1. [Finish working with the wizard](ahv_restore_disks_summary.md).

Page updated 2026-07-10

