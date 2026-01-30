---
title: "Detach-VBRBackup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/detach-vbrbackup.html"
last_updated: "1/7/2025"
product_version: "13.0.1.1071"
---

# Detach-VBRBackup


Short Description

Detaches backups from the job they belong to.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Detach-VBRBackup -Backup <CBackup[]> [-Force] [-Confirm] [-WhatIf]  [<CommonParameters>] |

Detailed Description

This cmdlet detaches backups from the job they belong to.

When the cmdlet detaches backups from a job, the job stops processing these backup files. During the next run, the job will start a new backups chain, that is, will create active full backups.

If the detached backups belonged to the job with daily retention, the background retention process retains the backups according to the configured retention and deletes the backups from the repository after the retention period ends. If the retention period is set in restore points, the background retention process does not delete the backups. You need to delete them manually using the [Remove-VBRBackup](remove-vbrbackup.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies an array of backups that you want to detach from a job. | Accepts the CBackup[] object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Force | Defines that the cmdlet will detach backups without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Detaching Backups from Job

This example shows how to detach backups from the Daily backups job.

|  |
| --- |
| $backup = Get-VBRBackup -Name "Daily backups"  Detach-VBRBackup -Backup $backup |

Perform the following steps:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the Detach-VBRBackup cmdlet. Set the $backup variable as the Backup parameter value.

Related Commands

[Get-VBRBackup](get-vbrbackup.md)


