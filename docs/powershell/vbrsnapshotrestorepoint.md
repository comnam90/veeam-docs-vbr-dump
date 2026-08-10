---
title: "VBRSnapshotRestorePoint"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrsnapshotrestorepoint.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VBRSnapshotRestorePoint


Contains a restore point of an InterSystems IRIS snapshot backup.

VBRSnapshotRestorePoint

| Property | Type | Description |
| Id | Guid | Specifies the ID of the restore point. |
| ObjectName | String | Specifies the name of the InterSystems IRIS instance for which the restore point was created. |
| BackupId | Guid | Specifies the ID of the snapshot backup to which the restore point belongs. |
| CreationTime | DateTime | Specifies the date and time when the restore point was created. |
| Algorithm | VBRAlgorithm | Specifies the backup algorithm of the restore point. |

Related Commands

* [Get-VBRSnapshotRestorePoint](get-vbrsnapshotrestorepoint.md)
* [Start-VBRIrisInstanceRestore](start-vbririsinstancerestore.md)
* [Get-VBRIrisInstanceOriginalPath](get-vbririsinstanceoriginalpath.md)

Page updated 2026-06-10

