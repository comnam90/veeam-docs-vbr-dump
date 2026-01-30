---
title: "Remove-VBRComputerBackupCopyJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrcomputerbackupcopyjob.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRComputerBackupCopyJob


Short Description

Removes Veeam Agent backup copy jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRComputerBackupCopyJob -Job <VBRComputerBackupCopyJob[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes Veeam Agent backup copy jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies a Veeam Agent backup copy job that you want to remove. | Accepts the VBRComputerBackupCopyJob object. To create this object, run the [Get-VBRComputerBackupCopyJob](get-vbrcomputerbackupcopyjob.md) cmdlet. | True | 0 | True(ByValue) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchPArameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchPArameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Veeam Agent Backup Copy Jobs

This example shows how to remove Veeam Agent backup copy job.

|  |
| --- |
| $job = Get-VBRComputerBackupCopyJob  Remove-VBRComputerBackupCopyJob -Job $job |

Perform the following steps:

1. Run the [Get-VBRComputerBackupCopyJob](get-vbrcomputerbackupcopyjob.md) cmdlet. Save the result to the $job variable.
2. Run the Remove-VBRComputerBackupCopyJob cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRComputerBackupCopyJob](get-vbrcomputerbackupcopyjob.md)


