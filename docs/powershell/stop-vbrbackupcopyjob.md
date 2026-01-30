---
title: "Stop-VBRBackupCopyJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrbackupcopyjob.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRBackupCopyJob


Short Description

Stops backup copy jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRBackupCopyJob -Job <VBRBackupCopyJob[]> [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet stops backup copy jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies a backup copy job that you want to stop. | Accepts the VBRBackupCopyJob[] object. To get this object, run the [Get-VBRBackupCopyJob](get-vbrbackupcopyjob.md) cmdlet. | True | 0 | True (ByPropertyName, ByValue) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Stopping Backup Copy Job

This example shows how to stop the backup copy job named Copy Job05.

|  |
| --- |
| $job = Get-VBRBackupCopyJob -Name "Copy Job05"  Stop-VBRBackupCopyJob -Job $job |

Perform the following steps:

1. Run the [Get-VBRBackupCopyJob](get-vbrbackupcopyjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the Stop-VBRBackupCopyJob cmdlet. Set the $job variable as the Job parameter value.

Related Commands

[Get-VBRBackupCopyJob](get-vbrbackupcopyjob.md)


