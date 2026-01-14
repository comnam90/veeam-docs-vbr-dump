---
title: "Get-VBRJobScheduleOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrjobscheduleoptions.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Get-VBRJobScheduleOptions

In this article

Short Description

Returns job scheduling settings.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRJobScheduleOptions -Job <CBackupJob[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns job scheduling options for a selected job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of jobs. The cmdlet will return scheduling options of these jobs. | Accepts the CBackupJob object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | 0 | True (ByProperty Name, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Looking for List of Scheduling Options of Specific Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to look for the list of scheduling options of the ActiveDirectory Copy Job job.  |  | | --- | | Get-VBRJob -Name "ActiveDirectory Copy Job" | Get-VBRJobScheduleOptions |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Get-VBRJobScheduleOptions cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Looking for List of Options of Job Represented by Variable

|  |  |
| --- | --- |
| This example shows how to look for the list of options of the job represented by the $activedirectory\_copy\_job variable.  |  | | --- | | $activedirectory\_copy\_job = Get-VBRJob -Name "ActiveDirectory Copy Job"  Get-VBRJobScheduleOptions -Job $activedirectory\_copy\_job |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $activedirectory\_copy\_job variable. 2. Run the Get-VBRJobScheduleOptions cmdlet. Set the $activedirectory\_copy\_job variable as the Job parameter value. |

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Get-VBRJobObject](get-vbrjobobject.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
