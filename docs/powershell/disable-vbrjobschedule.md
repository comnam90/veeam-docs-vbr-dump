---
title: "Disable-VBRJobSchedule"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrjobschedule.html"
last_updated: "6/12/2024"
product_version: "13.0.1.1071"
---

# Disable-VBRJobSchedule

In this article

Short Description

Disables job schedule.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRJobSchedule -Job <CBackupJob[]>  [<CommonParameters>] |

Detailed Description

This cmdlet disables job schedule. The schedule settings are not deleted. You can run this cmdlet with backup, replication and copy jobs.

Run the [Start-VBRJob](start-vbrjob.md) cmdlet to start the job once.

Run the [Enable-VBRJobSchedule](enable-vbrjobschedule.md) cmdlet to enable job schedule.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of jobs. The cmdlet will disable schedule in these jobs. | Accepts the CBackupJob object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByProperty Name, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Disabling Specific Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to disable the Backup Job 01 job.  |  | | --- | | Get-VBRJob -Name "Backup Job 01" | Disable-VBRJobSchedule |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Disable-VBRJobSchedule cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Disabling Job Represented by Variable

|  |  |
| --- | --- |
| This example shows how to disable the job represented by the $job variable.  |  | | --- | | $job = Get-VBRJob -Name "Backup Job 01"  Disable-VBRJobSchedule -Job $job |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Disable-VBRJobSchedule cmdlet. Set the $job variable as the Job parameter value. |

Related Commands

[Get-VBRJob](get-vbrjob.md)

Page updated 6/12/2024

Page content applies to build 13.0.1.1071
