---
title: "VBREntraIDBackupSecondaryTarget"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrentraidbackupsecondarytarget.html"
last_updated: "7/28/2025"
product_version: "13.0.1.1071"
---

# VBREntraIDBackupSecondaryTarget

In this article

Contains secondary repository settings for a Entra ID tenant backup job.

Properties

| Property | Type | Description |
| --- | --- | --- |
| BackupRepository | CBackupRepository | Backup repository used as a secondary target. |
| BackupWindow | VBRBackupWindowOptions | Specifies a time interval within which a backup job is allowed to create copies of Entra ID tenant backups. |
| CustomEncryptionKey | VBREncryptionKey | Encryption key used to encrypt data stored in the secondary repository. |
| CustomRetentionPeriod | Int32 | Retention period configured for the secondary repository. |
| CustomRetentionType | VBRUnstructuredBackupShortTermRetentionType | Retention policy configured for the secondary repository. |

Related Commands

* [New-VBREntraIDBackupSecondaryTarget](new-vbrentraidbackupsecondarytarget.md)
* [Set-VBREntraIDBackupSecondaryTarget](set-vbrentraidbackupsecondarytarget.md)

Page updated 7/28/2025

Page content applies to build 13.0.1.1071
