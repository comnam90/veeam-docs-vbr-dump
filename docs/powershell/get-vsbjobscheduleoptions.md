---
title: "Get-VSBJobScheduleOptions (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vsbjobscheduleoptions.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Get-VSBJobScheduleOptions (obsolete)

In this article

Short Description

Returns scheduling settings of a selected SureBackup job.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet will still work but may not be supported in further versions. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VSBJobScheduleOptions -Job <CSbJob> [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns scheduling options for a specified SureBackup job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the SureBackup job you want to get the scheduling settings of. | Accepts the CSbJob object. To get this object, run the [Get-VSBJob](get-vsbjob.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Scheduling Settings for Selected SureBackup Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to look for the list of scheduling settings for the SureJob 02 SureBackup job.  |  | | --- | | Get-VSBJob -Name "SureJob 02" | Get-VSBJobScheduleOptions |  Perform the following steps:   1. Run the [Get-VSBJob](get-vsbjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Get-VSBJobScheduleOptions cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Scheduling Settings for Selected SureBackup Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to look for the list of job settings for the SureJob 02 SureBackup job.  |  | | --- | | $SureJob = Get-VSBJob -Name "SureJob 02"  Get-VSBJobScheduleOptions -Job $SureJob |  Perform the following steps:   1. Run the [Get-VSBJob](get-vsbjob.md) cmdlet. Specify the Name parameter value. Save the result to the $SureJob variable. 2. Run the Get-VSBJobScheduleOptions cmdlet. Set the $SureJob variable as the Job parameter value. |

Related Commands

[Get-VSBJob](get-vsbjob.md)

Page updated 3/11/2024

Page content applies to build 13.0.1.1071
