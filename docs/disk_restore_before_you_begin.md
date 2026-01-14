---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/disk_restore_before_you_begin.html"
last_updated: "1/25/2024"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

Before you restore virtual disks, check the following prerequisites:

* You can restore virtual disks from a backup that has at least one successfully created restore point.
* During the virtual disk restore, Veeam Backup & Replication turns off the target VM to reconfigure its settings and attach restored disks. It is recommended that you stop all activities on the target VM for the restore period.
* If you want to scan virtual disk data for viruses, check the [secure restore requirements and limitations](av_scan_about.md#av_limitations).

|  |
| --- |
| Note |
| If you back up a VM with vRDM disks, Veeam Backup & Replication converts them into VMDK files. Thus, when you restore a vRDM disk, Veeam Backup & Replication will restore it as a VMDK file. If you want to preserve the vRDM format for restored disks, use Quick Rollback. For more information, see [Quick Rollback](incremental_restore.md). |

Page updated 1/25/2024

Page content applies to build 13.0.1.1071
