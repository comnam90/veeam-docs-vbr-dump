---
title: "VBRBackupObject"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrbackupobject.html"
last_updated: "7/17/2024"
product_version: "13.0.1.1071"
---

# VBRBackupObject

In this article

Contains VM backup or replica object settings.

Properties

| Property | Type | Description |
| --- | --- | --- |
| BackupId | Guid | Parent job ID |
| ObjectId | Guid | Backup or replica object ID |
| RestorePointsCount | Int | Number of restore points |
| RepositoryId | Guid | Repository ID |
| Platform | VBRPlatform | Platform |
| PlatformId | Guid | Platform ID |
| CreationTime | DateTime | Date when the backup or replica was created |
| IsLinux | Boolean | Indicates if the VM has Linux OS |
| Name | String | Source VM name |
| Id | Guid | VM ID in the backup or replica ID |

Related Commands

[Get-VBRBackupObject](get-vbrbackupobject.md)

Page updated 7/17/2024

Page content applies to build 13.0.1.1071
