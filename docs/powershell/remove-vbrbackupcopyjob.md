---
title: "Remove-VBRBackupCopyJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrbackupcopyjob.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRBackupCopyJob


Short Description

Removes backup copy jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRBackupCopyJob -Job <VBRBackupCopyJob[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes backup copy jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of backup copy jobs that you want to remove. | Accepts the VBRBackupCopyJob[] object. To create this object, run the [Get-VBRBackupCopyJob](get-vbrbackupcopyjob.md) cmdlet. | True | 0 | True(ByValue, ByPropertyName) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Backup Copy Job

This example shows how to remove a backup copy job.

|  |
| --- |
| $job = Get-VBRBackupCopyJob  Remove-VBRBackupCopyJob -Job $job |

Perform the following steps:

1. Run the [Get-VBRBackupCopyJob](get-vbrbackupcopyjob.md) cmdlet. Save the result to the $job variable.
2. Run the Remove-VBRBackupCopyJob cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRBackupCopyJob](get-vbrbackupcopyjob.md)


