---
title: "Start-VSBJob (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vsbjob.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Start-VSBJob (obsolete)

In this article

Short Description

Starts a created SureBackup job.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Start-VBRSureBackupJob](start-vbrsurebackupjob.md) cmdlet instead. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VSBJob -Job <CSbJob[]> [-RunAsync] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet allows you to start a created SureBackup job.

When you create a job, you need to run it manually unless you enable a job schedule. Run the [Set-VSBJobSchedule](set-vsbjobschedule.md) cmdlet to schedule the SureBackup job to run automatically.

Run the [Stop-VSBJob](stop-vsbjob.md) cmdlet to stop a running SureBackup job.

Run the [Start-VBRJob](start-vbrjob.md) cmdlet to start a backup, replication or copy job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of the SureBackup jobs. The cmdlet will start these jobs. | Accepts the CSbJob[] object. To get this object, run the [Get-VSBJob](get-vsbjob.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Starting Selected SureBackup Jobs [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to start the SharePoint SureJob 01 and SharePoint SureJob 02 jobs.  |  | | --- | | Get-VSBJob -Name "SharePoint SureJob 01", "SharePoint SureJob 02" | Start-VSBJob |  Perform the following steps:   1. Run the [Get-VSBJob](get-vsbjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Start-VSBJob cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Starting Selected SureBackup Jobs [Using Variable]

|  |  |
| --- | --- |
| This example shows how to start the SharePoint SureJob 01 and SharePoint SureJob 02 jobs.  |  | | --- | | $SureJob = Get-VSBJob -Name "SharePoint SureJob 01", "SharePoint SureJob 02"  Start-VSBJob -Job $SureJob |  Perform the following steps:   1. Run the [Get-VSBJob](get-vsbjob.md) cmdlet. Specify the Name parameter value. Save the result to the $SureJob variable. 2. Run the Start-VSBJob cmdlet. Set the $SureJob variable as the Job parameter value. |

Related Commands

[Get-VSBJob](get-vsbjob.md)

Page updated 3/11/2024

Page content applies to build 13.0.1.1071
