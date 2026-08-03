---
title: "VESQLRDSRestorePoint"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vesqlrdsrestorepoint.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VESQLRDSRestorePoint


Contains details about a restore point of a backed-up Microsoft SQL Server database running on Amazon RDS.

VESQLRDSRestorePoint

| Property | Type | Description |
| Id | GUID | Restore point ID. |
| BackupTime | DateTime | Date and time when the restore point was created. |
| LastLsn | String | The log sequence number (LSN) of the last transaction in the restore point. |
| BackupType | VESQLRDSBackupType | Backup type. Possible values:   * Unknown * Full * Differential * Log |

Related Commands

[Get-VESQLRDSRestorePoint](get-vesqlrdsrestorepoint.md)

Page updated 2026-01-27

