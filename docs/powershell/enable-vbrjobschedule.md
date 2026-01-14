---
title: "Enable-VBRJobSchedule"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrjobschedule.html"
last_updated: "6/12/2024"
product_version: "13.0.1.1071"
---

# Enable-VBRJobSchedule

In this article

Short Description

Enables job schedule.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRJobSchedule -Job <CBackupJob[]>  [<CommonParameters>] |

Detailed Description

This cmdlet enables job schedule.

You can enable the job schedule in case you have the schedule configured for this job. You can run this cmdlet with any kind of jobs.

Run the [Disable-VBRJobSchedule](disable-vbrjobschedule.md) cmdlet to disable job schedule.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of jobs. The cmdlet will enable schedule in these jobs. | Accepts the CBackupJob object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByProperty Name. ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Enabling Specific Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to enable the schedule for Backup Job 01 and File Copy Job 02 jobs.  |  | | --- | | Get-VBRJob -Name "Backup Job 01", "File Copy Job 02" | Enable-VBRJobSchedule |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Enable-VBRJobSchedule cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Disabling Job Represented by Variable

|  |  |
| --- | --- |
| This example shows how to enable the schedule for job represented by the $BackupJob01 variable.  |  | | --- | | $BackupJob01 = Get-VBRJob -Name "Backup Job 01"  Enable-VBRJobSchedule -Job $BackupJob01 |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $BackupJob01 variable. 2. Run the Enable-VBRJobSchedule cmdlet. Set the $BackupJob01 variable as the Job parameter value. |

Related Commands

[Get-VBRJob](get-vbrjob.md)

Page updated 6/12/2024

Page content applies to build 13.0.1.1071
