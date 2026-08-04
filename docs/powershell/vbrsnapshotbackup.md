---
title: "VBRSnapshotBackup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrsnapshotbackup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VBRSnapshotBackup


Contains an InterSystems IRIS snapshot backup.

VBRSnapshotBackup

| Property | Type | Description |
| Id | Guid | Specifies the ID of the snapshot backup. |
| Name | String | Specifies the name of the snapshot backup. |
| JobId | Guid | Specifies the ID of the application backup policy that created the snapshot backup. |
| Platform | VBRPlatform | Specifies the platform of the snapshot backup. |
| CreationTime | DateTime | Specifies the date and time when the snapshot backup was created. |

Related Commands

* [Get-VBRSnapshotBackup](get-vbrsnapshotbackup.md)
* [Get-VBRSnapshotRestorePoint](get-vbrsnapshotrestorepoint.md)

Page updated 2026-06-10

