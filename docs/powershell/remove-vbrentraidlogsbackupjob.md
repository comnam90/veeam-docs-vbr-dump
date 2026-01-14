---
title: "Remove-VBREntraIDLogsBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrentraidlogsbackupjob.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Remove-VBREntraIDLogsBackupJob

In this article

Short Description

Removes Microsoft Entra ID log backup jobs.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBREntraIDLogsBackupJob -Job <VBREntraIdLogsBackupJob[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes backup jobs that protect Entra ID audit and sign-in logs.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of log backup jobs that you want to remove. | Accepts the VBREntraIdLogsBackupJob[] object. To get this object, run the [Get-VBREntraIdLogsBackupJob](get-vbrentraidlogsbackupjob.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing Entra ID Log Backup Job

This example shows how to remove the Log Backup backup job.

|  |
| --- |
| $logBackupJob = Get-VBREntraIDLogsBackupJob -Name "Log Backup"  Remove-VBREntraIDLogsBackupJob -Job $logBackupJob |

Perform the following steps:

1. Run the [Get-VBREntraIDLogsBackupJob](get-vbrentraidlogsbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $backupJob variable.
2. Run the Remove-VBREntraIDLogsBackupJob cmdlet. Set the $backupJob variable as the Job parameter value.

Related Commands

[Get-VBREntraIDLogsBackupJob](get-vbrentraidlogsbackupjob.md)

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
