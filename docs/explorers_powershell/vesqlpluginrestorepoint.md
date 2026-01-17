---
title: "VESQLPluginRestorePoint"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vesqlpluginrestorepoint.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---

# VESQLPluginRestorePoint


Contains details about a restore point of a database backed up with Veeam Plug-in for Microsoft SQL Server.

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Restore point ID. |
| BackupTime | DateTime | Date and time when the restore point was created. |
| LastLsn | String | The log sequence number (LSN) of the last transaction in the restore point. |
| BackupType | VESQLPluginBackupType | Backup type. Possible values:   * Unknown * Full * Differential * Log |
| BackupSet | String | Backup set name. You can specify this value when creating a backup with a standalone plug-in. For backups created by a managed plug-in, this value is the same as the backup job name. |
| Description | String | Backup set description. You can specify this value when creating a backup with a standalone plug-in. For backups created by a managed plug-in, this value is "<backup\_job\_name> backups". |

Related Commands

[Get-VESQLPluginRestorePoint](get-vesqlpluginrestorepoint.md)


