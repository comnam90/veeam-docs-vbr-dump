---
title: "Backup Repositories with Rotated Drives"
source_url: "https://helpcenter.veeam.com/docs/vbr/userguide/backup_repository_rotated.html"
last_updated: "3/28/2025"
product_version: "13.0.1.1071"
---

# Backup Repositories with Rotated Drives

In this article

A backup repository can use rotated drives. Rotated drives can be detachable USB or eSATA hard drives. This scenario can be helpful if you want to store backups on several external hard drives that you plan to regularly move between different locations.

To use rotated drives, you must enable the This repository is backed by rotated hard drives option in the advanced settings of the backup repository. When this option is enabled, Veeam Backup & Replication recognizes the backup target as a backup repository with rotated drives and uses a specific algorithm to make sure that the backup chain created on these drives is not broken.

Limitations for Backup Repositories with Rotated Drives

Backup repositories with rotated drives have the following limitations:

* On one managed server, you must create only one repository with rotated drives.
* The automount feature must be enabled on the Microsoft Windows server added as a a backup repository with rotated drives. This feature enables Microsoft Windows to assign the partition letter each time you swap the external hard drives. For more information, see [Microsoft Docs](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/automount).
* You cannot store archive full backups (GFS backups) created with backup jobs or backup copy jobs in backup repositories with rotated drives.
* You cannot rescan backup repositories with rotated drives.
* NFS backup repositories do not support rotated drives. If you enable the This repository is backed by rotated hard drives setting on the repository, Veeam Backup & Replication will ignore this setting.
* Scale-out backup repositories do not support rotated drives. If you enable the This repository is backed by rotated hard drives setting on an extent, Veeam Backup & Replication will ignore this setting and will work with such repository as with a standard extent.
* Repositories with rotated drives are not supported as [archive repositories](unstructured_data_backup.md#backup_repository) for unstructured data backup.
* [Background retention](background_retention_job.md) doesn't apply to the backups stored on backup repositories with rotated drives. These backup files will not be deleted by the retention job.
* [For Veeam Cloud Connect users] Veeam Backup & Replication does not support the use of backup repositories with rotated drives as cloud repositories.

In This Section

* [How Repository with Rotated Drives Works](rotated_drives_hiw.md)
* [Deploying Backup Repositories with Rotated Drives](rotated_drives_configure.md)

Page updated 3/28/2025

Page content applies to build 13.0.1.1071
