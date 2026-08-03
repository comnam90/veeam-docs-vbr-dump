---
title: "VBRTapeDbPluginRestorePoint"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrtapedbpluginrestorepoint.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VBRTapeDbPluginRestorePoint


Contains information about a restore point of a database application backup stored on tape.

VBRTapeDbPluginRestorePoint

| Property | Type | Description |
| BackupSetId | Guid | Specifies the ID of the backup set. |
| BackupId | Guid | Specifies the ID of the backup. |
| PointWriteTimeUtc | DateTime | Specifies the date and time when the restore point was written, in UTC. |
| BackupSetCreationTime | DateTime | Specifies the date and time when the backup set was created. |
| Type | String | Specifies the type of the restore point. |
| MediaPoolName | String | Specifies the name of the media pool. |
| MediaSet | String | Specifies the name of the media set. |
| LibrariesNames | String[] | Specifies an array of names of the tape libraries. |
| TapeMediaNames | String[] | Specifies an array of names of the tape media. |

Related Commands

[Get-VBRTapeDbPluginRestorePoint](get-vbrtapedbpluginrestorepoint.md)

Page updated 2026-06-05

