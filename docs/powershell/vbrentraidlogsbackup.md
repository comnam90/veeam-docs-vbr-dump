---
title: "VBREntraIDLogsBackup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrentraidlogsbackup.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# VBREntraIDLogsBackup


Contains details on a backup of Microsoft Entra ID audit and sign-in logs.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | Guid | Backup ID. |
| Name | String | Backup name. |
| JobId | Guid | Backup job information. |
| CreationTime | DateTime | Date and time when the backup was created. |
| LastRestorePointCreationTime | DateTime | Date and time when the last restore point was created. |
| IsEncrypted | Boolean | Defines that the backup is encrypted. |

Related Commands

[Get-VBREntraIDLogsBackup](get-vbrentraidlogsbackup.md)


