---
title: "Before You Begin"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/image_create_before.html"
last_updated: "8/22/2025"
product_version: "13.0.1.1071"
---

# Before You Begin

In this article

You can create a Veeam Recovery Media for a protected computer in Veeam Backup & Replication if the following conditions are met:

* A protected computer runs a Microsoft Windows OS.

* A full backup file of one of the following backup types was created for the protected computer on the target location by a Veeam Agent backup job:

* Entire computer backup
* Volume-level backup of the computer OS data (created with the Operating system option selected in the backup job settings) or computer system volume
* File-level backup of the computer OS data created with the Operating system option selected in the backup job settings

|  |
| --- |
| NOTE |
| * You can create a Veeam Recovery Media for a protected computer using a copy of a full backup file that meets all the conditions. To learn more, see the [Backup Copy](backup_copy.md).  * By default, you cannot create a Veeam Recovery Media for a failover cluster with Cluster Shared Volumes (CSV). As a workaround, you can create a Veeam Recovery Media directly on the failover cluster node. To learn more, see [this Veeam KB article](https://www.veeam.com/kb2058). |

Removable Storage Device Scenario (USB, SD Card and Other)

* The removable storage device must be inserted into a corresponding slot on the computer or connected to the computer.
* The removable storage device must have enough capacity to store the created recovery image. On average, the size of the created recovery image without manually loaded drivers is 500 MB.
* During the recovery image creation, Veeam Agent for Microsoft Windows formats the removable storage device. If you have important information on the device, create a copy of this data in some other location.

Page updated 8/22/2025

Page content applies to build 13.0.1.1071
