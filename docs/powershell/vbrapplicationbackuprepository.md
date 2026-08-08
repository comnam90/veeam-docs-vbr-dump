---
title: "VBRApplicationBackupRepository"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrapplicationbackuprepository.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VBRApplicationBackupRepository


Contains information about an application backup repository added to the backup infrastructure.

VBRApplicationBackupRepository

| Property | Type | Description |
| Server | CHost | Specifies the server that hosts the application backup repository. |
| ZFSPool | String | Specifies the ZFS storage resource pool that contains application backup policy files. |
| MountPath | String | Specifies the mount path to the NFS share. |
| RepositoryPermissions | VBRApplicationBackupRepositoryPermission[] | Specifies host permissions configured for the application backup repository. |
| KerberosPermissions | VBRApplicationBackupRepositoryKerberosPermission[] | Specifies Kerberos permissions configured for the application backup repository. |
| ScheduleOptions | VBRApplicationBackupRepositoryScheduleOptions | Specifies snapshot creation schedule settings for the application backup repository. |
| NotificationOptions | VBRNotificationOptions | Specifies notification settings for the application backup repository. |
| RetentionDays | Int32 | Specifies the number of days for the snapshot retention policy. |

Related Commands

* [Get-VBRApplicationBackupRepository](get-vbrapplicationbackuprepository.md)
* [Add-VBRApplicationBackupRepository](add-vbrapplicationbackuprepository.md)

Page updated 2026-05-27

