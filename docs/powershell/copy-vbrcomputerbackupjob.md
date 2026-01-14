---
title: "Copy-VBRComputerBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/copy-vbrcomputerbackupjob.html"
last_updated: "3/6/2024"
product_version: "13.0.1.1071"
---

# Copy-VBRComputerBackupJob

In this article

Short Description

Clones Veeam Agent backup jobs and Veeam Agent backup policies.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Copy-VBRComputerBackupJob -Job <VBRComputerBackupJob[]> [-Name <string[]>] [-Description <string[]>] [-Repository <CBackupRepository>]  [<CommonParameters>] |

Detailed Description

This cmdlet clones Veeam Agent backup jobs and Veeam Agent backup policies.

|  |
| --- |
| ![Copy-VBRComputerBackupJob](images/icon_important.webp) Important! |
| The job cloning functionality is available only in the Enterprise and Enterprise Plus, Veeam Universal License editions of Veeam Backup & Replication. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies a Veeam Agent backup job or a Veeam Agent backup policy that you want to clone. | Accepts the VBRComputerBackupJob[] object. To get this object, run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| Name | Specifies a name of a cloned Veeam Agent backup job or a Veeam Agent backup policy. | String[] | False | Named | False |
| Description | Specifies a description of a cloned Veeam Agent backup job or a Veeam Agent backup policy. | String[] | False | Named | False |
| Repository | Specifies a backup repository. The cmdlet will keep backups of a cloned Veeam Agent backup job or a Veeam Agent backup policy on this backup repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRComputerBackupJob object that contains settings of cloned Veeam Agent backup jobs and of Veeam Agent backup policies.

Examples

Cloning Veeam Agent Backup Job

This example shows how to clone the WinSrv2049 Veeam Agent backup job.

|  |
| --- |
| $job = Get-VBRComputerBackupJob -Name "WinSrv2049"  Copy-VBRComputerBackupJob -Job $job |

Perform the following steps:

1. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Copy-VBRComputerBackupJob cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md)

Page updated 3/6/2024

Page content applies to build 13.0.1.1071
