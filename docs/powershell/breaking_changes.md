---
title: "Breaking Changes"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/breaking_changes.html"
last_updated: "2/9/2024"
product_version: "13.0.1.1071"
---

# Breaking Changes

In this article

This section contains information on breaking changes in Veeam PowerShell v12. These changes cause Veeam PowerShell v12 to function differently and could affect the client code.

Backup Copy Job

In this version, you can no longer use the In this version, [Start-VBRJob](start-vbrjob.md) to start backup copy jobs. Run the [Sync-VBRBackupCopyJob](sync-vbrbackupcopyjob.md) instead.

Deprecated Cmdlets

The following cmdlets are deprecated in Veeam PowerShell v12. To perform the necessary actions, run new cmdlets instead.

| Deprecated Cmdlets | New Cmdlets |
| --- | --- |
| [Add-VBRComputerBackupCopyJob](add-vbrcomputerbackupcopyjob.md) | [Add-VBRBackupCopyJob](add-vbrbackupcopyjob.md) |
| [Copy-VBRComputerBackupCopyJob](copy-vbrcomputerbackupcopyjob.md) | [Copy-VBRBackupCopyJob](copy-vbrbackupcopyjob.md) |
| [Add-VBRAzureComputeBackupCopyJob](add-vbrazurecomputebackupcopyjob.md) | [Add-VBRBackupCopyJob](add-vbrbackupcopyjob.md) |
| [Add-VBREC2BackupCopyJob](add-vbrec2backupcopyjob.md) | [Add-VBRBackupCopyJob](add-vbrbackupcopyjob.md) |
| [Add-VBREpBackupCopyJob](add-vbrepbackupcopyjob.md) | Applies only for creating a simple mode backup copy job. For other scenarios, run the [Add-VBRBackupCopyJob](add-vbrbackupcopyjob.md) cmdlet. |
| [Add-VBRHvBackupCopyJob](add-vbrhvbackupcopyjob.md) | Applies only for creating a simple mode backup copy job. For other scenarios, run the [Add-VBRBackupCopyJob](add-vbrbackupcopyjob.md) cmdlet. |
| [Add-VBRvCloudBackupCopyJob](add-vbrvcloudbackupcopyjob.md) | Applies only for creating a simple mode backup copy job. For other scenarios, run the [Add-VBRBackupCopyJob](add-vbrbackupcopyjob.md) cmdlet. |

Page updated 2/9/2024

Page content applies to build 13.0.1.1071
