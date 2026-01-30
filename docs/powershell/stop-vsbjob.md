---
title: "Stop-VSBJob (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vsbjob.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Stop-VSBJob (obsolete)


Short Description

Stops running SureBackup job.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Stop-VBRSureBackupJob](stop-vbrsurebackupjob.md) cmdlet instead. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VSBJob -Job <CSbJob[]> [-RunAsync] [-WarningAction <ActionPreference>] [-WarningVariable <String>] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet stops a running SureBackup job. The job is stopped once, the scheduled SureBackup job will start the next scheduled time.

Run the [Start-VSBJob](start-vsbjob.md) cmdlet to start the job manually.

Run the [Stop-VBRJob](stop-vbrjob.md) cmdlet to stop a backup, replication or copy job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of the SureBackup jobs. The cmdlet will stop these jobs. | Accepts the CSbJob[] object. To get this object, run the [Get-VSBJob](get-vsbjob.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Stopping Specific SureBackup Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to stop the AD SureJob SureBackup job.  |  | | --- | | Get-VSBJob -Name "AD SureJob" | Stop-VSBJob |  Perform the following steps:   1. Run the Get-VSBJob cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Stop-VSBJob cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Stopping Specific SureBackup Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to stop the AD SureJob SureBackup job.  |  | | --- | | $ADSureJob = Get-VSBJob -Name "AD SureJob"  Stop-VSBJob -Job $ADSureJob |  Perform the following steps:   1. Run the Get-VSBJob cmdlet. Specify the Name parameter value. Save the result to the $ADSureJob variable. 2. Run the Stop-VSBJob cmdlet. Set the $ADSureJob variable as the Job parameter value. |

Related Commands

[Get-VSBJob](get-vsbjob.md)


