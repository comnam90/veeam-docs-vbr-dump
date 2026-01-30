---
title: "VBRMoveBackupSession"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrmovebackupsession.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRMoveBackupSession


This object contains settings of the move session.

Properties

| Property | Type | Description |
| --- | --- | --- |
| TargetRepositoryID | GUID | ID of the target repository. |
| TargetPath | string | Path to the target folder. |
| Backup | GUID[] | ID of the backup that will be moved. |

Related Commands

[Move-VBRBackup](move-vbrbackup.md)


