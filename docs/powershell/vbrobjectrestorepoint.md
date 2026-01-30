---
title: "VBRObjectRestorePoint"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrobjectrestorepoint.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# VBRObjectRestorePoint


Contains restore points created by jobs.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | Guid | Restore points ID. |
| Name | String | Restore points name. |
| BackupId | Guid | VM names. |
| CreationDate | DateTime | Date of restore point scan. |
| ObjectId | Guid | IDs of backed-up hosts and VMs. |
| Status | [VBRActivitySeverity](enums.md#VBRActivitySeverity) | Backup malware state. |

Related Commands

[Get-VBRObjectRestorePoint](get-vbrobjectrestorepoint.md)


