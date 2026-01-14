---
title: "Remove-VBRJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrjob.html"
last_updated: "12/16/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRJob

In this article

Short Description

Removes a selected backup, replication or backup copy job.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRJob -Job <CBackupJob[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes a selected backup, replication or tape job from Veeam Backup & Replication console and database.

Run the [Remove-VBRBackupCopyJob](remove-vbrbackupcopyjob.md) cmdlet to remove backup copy jobs.

Run the [Remove-VSBJob](remove-vsbjob.md) cmdlet to remove SureBackup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of jobs you want to remove. | Accepts the CBackupJob object. To get this object, run the [Get-VBRJob](get-vbrjob.md) or [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. | True | 0 | True (ByValue, ByProperty Name) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing File Copy Jobs [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to remove the file copy jobs.  |  | | --- | | Get-VBRJob -Name "File Copy\*" | Remove-VBRJob |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Remove-VBRJob cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Specific Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to remove the job represented by the $job variable.  |  | | --- | | $job = Get-VBRJob -Name "Backup Job"  Remove-VBRJob -Job $job |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Remove-VBRJob cmdlet. Set the $job variable as the Job parameter value. |

Related Commands

[Get-VBRJob](get-vbrjob.md)

Page updated 12/16/2025

Page content applies to build 13.0.1.1071
