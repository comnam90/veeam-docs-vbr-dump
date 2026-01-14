---
title: "Remove-VBRComputerBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrcomputerbackupjob.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRComputerBackupJob

In this article

Short Description

Removes Veeam Agent backup jobs and Veeam Agent backup policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRComputerBackupJob -Job <VBRComputerBackupJob[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes Veeam Agent backup jobs and Veeam Agent backup policies from Veeam Backup & Replication infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies a Veeam Agent backup job or a Veeam Agent backup policy that you want to remove. | Accepts the VBRComputerBackupJob[] object. To get this object, run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Veeam Agent Backup Jobs

This cmdlet shows how to remove the WinSrv2049 Veeam Agent backup job from Veeam Backup & Replication infrastructure.

|  |
| --- |
| $job = Get-VBRComputerBackupJob -Name "WinSrv2049"  Remove-VBRComputerBackupJob -Job $job |

Perform the following steps:

1. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Remove-VBRComputerBackupJob cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md)

Page updated 5/7/2024

Page content applies to build 13.0.1.1071
