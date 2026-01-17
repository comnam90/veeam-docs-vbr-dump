---
title: "VBRSiteCollectionRestorePoint"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vbrsitecollectionrestorepoint.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---

# VBRSiteCollectionRestorePoint


Contains details about a restore point of a backed-up Microsoft SQL Server database for a Microsoft SharePoint site collection.

| Property | Type | Description |
| --- | --- | --- |
| URL | String | Site URL. |
| RestorePointID | GUID | Restore point ID. |
| SqlRestorePointId | GUID | Microsoft SQL Server database restore point ID. |
| DatabaseName | String | SharePoint database name. |
| CreationTime | DateTime | Date and time when the restore points was created. |
| Type | VBRRestorePointType | Restore point type. Possible values:   * Full * Rollback * Increment * Different * Snapshot |
| BackupName | String | Backup name. |
| Id | GUID | Site collection ID. |

Related Commands

[Get-VBRSiteCollectionRestorePoint](get-vbrsitecollectionrestorepoint.md)


