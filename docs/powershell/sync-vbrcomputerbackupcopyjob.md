---
title: "Sync-VBRComputerBackupCopyJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-vbrcomputerbackupcopyjob.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Sync-VBRComputerBackupCopyJob

In this article

Short Description

Synchronizes Veeam Agent backup copy jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Sync-VBRComputerBackupCopyJob -Job <VBRComputerBackupCopyJob> [-FullBackup] [-ImmediateCopyLastRestorePoint]  [<CommonParameters>] |

Detailed Description

This cmdlet synchronizes Veeam Agent backup copy jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the Veeam Agent backup copy job. The cmdlet will synchronize this job. | Accepts the VBRComputerBackupCopyJob object. To create this object, run the [Get-VBRComputerBackupCopyJob](get-vbrcomputerbackupcopyjob.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| FullBackup | Defines that the job will create an active full backup. | SwitchParameter | False | Named | False |
| ImmediateCopyLastRestorePoint | Defines that the job will create restore points as soon as they appear in a source backup repository. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRComputerBackupCopyJob object that contains settings of synchronized Veeam Agent backup copy jobs.

Examples

Synchronizing Veeam Agent Backup Copy Job

This example shows how to synchronize the Windows Copy Job05 Veeam Agent backup copy jobs.

|  |
| --- |
| $job = Get-VBRComputerBackupCopyJob -Name "Windows Copy Job05"  Sync-VBRComputerBackupCopyJob -Job $job |

Perform the following steps:

1. Run the [Get-VBRComputerBackupCopyJob](get-vbrcomputerbackupcopyjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Sync-VBRComputerBackupCopyJob cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRComputerBackupCopyJob](get-vbrcomputerbackupcopyjob.md)

Page updated 3/1/2024

Page content applies to build 13.0.1.1071
