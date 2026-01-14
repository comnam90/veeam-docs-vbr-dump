---
title: "Virtual Disk Restore"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/virtual_drive_recovery.html"
last_updated: "8/7/2025"
product_version: "13.0.1.1071"
---

# Virtual Disk Restore

In this article

Veeam Backup & Replication allows you to recover individual virtual disks of a VM from a backup. Recovered virtual disks can be attached to the original VM (for example, if you want to replace a corrupted disk) or mapped to any other VM in the virtual infrastructure. This recovery option can be helpful if a VM disk becomes corrupted.

You can restore VM virtual disk to the latest state or any valid restore point. You can preserve the format of a recovered virtual disk or convert it to the thin or thick provisioned disk format.

|  |
| --- |
| Note |
| If a VM has several VM disks, Veeam Backup & Replication restores VM disks in parallel. |

Related Resources

* [Restoring Virtual Disks](performing_disk_restore.md)

* [Restoring Volumes from Veeam Agent Backups](integration_volume_restore.md)

Page updated 8/7/2025

Page content applies to build 13.0.1.1071
