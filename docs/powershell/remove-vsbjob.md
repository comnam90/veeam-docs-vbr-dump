---
title: "Remove-VSBJob (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vsbjob.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Remove-VSBJob (obsolete)


Short Description

Removes a specified SureBackup job.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Remove-VBRSureBackupJob](remove-vbrsurebackupjob.md) cmdlet instead. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VSBJob -Job <CSbJob[]> [-WarningAction <ActionPreference>] [-WarningVariable <String>] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes a specified SureBackup job from Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of SureBackup jobs. The cmdlet will remove these jobs. | Accepts the CSbJob[] object. To get this object, run the [Get-VSBJob](get-vsbjob.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Selected SureBackup Jobs [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to remove the SureJob 01 and SureJob 12 SureBackup jobs.  |  | | --- | | Get-VSBJob -Name "SureJob 01", "SureJob 12"| Remove-VSBJob |  Perform the following steps:   1. Run the [Get-VSBJob](get-vsbjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Remove-VSBJob cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Selected SureBackup Jobs [Using Variable]

|  |  |
| --- | --- |
| This example shows how to remove the Fileserver Backup backup session.  |  | | --- | | $surejob = Get-VSBJob -Name "SureJob 01", "SureJob 12"  Remove-VSBJob -Job $surejob |  Perform the following steps:   1. Run the [Get-VSBJob](get-vsbjob.md) cmdlet. Specify the Name parameter value. Save the result to the $surejob variable. 2. Run the Remove-VSBJob cmdlet. Set the $surejob as the Job parameter value. |

Related Commands

[Get-VSBJob](get-vsbjob.md)


