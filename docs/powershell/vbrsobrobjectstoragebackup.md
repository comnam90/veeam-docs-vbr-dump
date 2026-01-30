---
title: "VBRSOBRObjectStorageBackup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrsobrobjectstoragebackup.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# VBRSOBRObjectStorageBackup


Contains settings of backups located on capacity extents and archive extents of scale-out backup repositories.

Properties

| Property | Type | Description |
| --- | --- | --- |
| JobId | Guid | Job ID |
| RepositoryId | Guid | Repository ID |
| CreationTime | DateTime | Date and time the backup was created |
| Platform | VBRPlatform | Visualization platform |
| IsCapacity | bool | Defines capacity tier |
| IsArchive | bool | Defines archive tier |
| IsEncrypted | bool | Defines that the backup is encrypted |

Related Commands

[Get-VBRSOBRObjectStorageRestorePoint](get-vbrsobrobjectstoragerestorepoint.md)


