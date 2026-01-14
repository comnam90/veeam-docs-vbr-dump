---
title: "VBRSOBRObjectStorageRestorePoint"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrsobrobjectstoragerestorepoint.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# VBRSOBRObjectStorageRestorePoint

In this article

Contains settings of machines restore points stored on archive extents or capacity extents of a scale-out backup repository.

Properties

| Property | Type | Description |
| --- | --- | --- |
| IsArchive | bool | Defines that the restore point is stored on archive extent. |
| IsCapacity | bool | Defines that the restore point is stored on capacity extent. |
| BackupId | Guid | ID of a restore |
| ObjectId | Guid | ID of a backed-up machines |

Related Commands

[Get-VBRSOBRObjectStorageRestorePoint](get-vbrsobrobjectstoragerestorepoint.md)

Page updated 2/16/2024

Page content applies to build 13.0.1.1071
