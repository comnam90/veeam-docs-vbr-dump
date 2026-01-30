---
title: "VBRNASBackupRestorePoint"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrnasbackuprestorepoint.html"
last_updated: "1/17/2024"
product_version: "13.0.1.1071"
---

# VBRNASBackupRestorePoint


Contains settings of restore points created by the file backup jobs.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Restore point ID. |
| NASServerId | GUID | File share ID. |
| NASServerName | String | File share name. |
| BackupId | GUID | Backup ID. |
| CreationTime | DateTime | Date and time of session creation. |
| Type | VBRNASBackupRestorePointType | Type of the restore point. |

Related Commands

[Get-VBRNASBackupRestorePoint](get-vbrnasbackuprestorepoint.md)


