---
title: "Remove-VBRSureBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrsurebackupjob.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRSureBackupJob


Short Description

Removes SureBackup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRSureBackupJob -Job <VBRSureBackupJobBase[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes SureBackup jobs from the Veeam Backup & Replication infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies an array of SureBackup jobs. The cmdlet will remove these jobs from the Veeam Backup & Replication infrastructure. | Accepts the VBRSureBackupJobBase[] object. To create this object, run the [Get-VBRSureBackupJob](get-vbrsurebackupjob.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParamter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if the user is sure that he wants to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing All SureBackup Jobs

|  |  |
| --- | --- |
| This example shows how to remove all SureBackup jobs from the Veeam Backup & Replication infrastructure.  |  | | --- | | $job = Get-VBRSureBackupJob  Remove-VBRSureBackupJob -Job $job |  Perform the following steps:   1. Run the [Get-VBRSureBackupJob](get-vbrsurebackupjob.md) cmdlet. Save the result to the $job variable. 2. Run the Remove-VBRSureBackupJob cmdlet. Set the $job variable as the Job parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Specific SureBackup Jobs

|  |  |
| --- | --- |
| This example shows how to remove the SureJob 2 SureBackup jobs from the Veeam Backup & Replication infrastructure.  |  | | --- | | $job = Get-VBRSureBackupJob -Name "SureJob 2"  Remove-VBRSureBackupJob -Job $job |  Perform the following steps:   1. Run the [Get-VBRSureBackupJob](get-vbrsurebackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Remove-VBRSureBackupJob cmdlet. Set the $job variable as the Job parameter value. |

Related Commands

[Get-VBRSureBackupJob](get-vbrsurebackupjob.md)


