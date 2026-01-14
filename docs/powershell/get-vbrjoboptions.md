---
title: "Get-VBRJobOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrjoboptions.html"
last_updated: "7/16/2025"
product_version: "13.0.1.1071"
---

# Get-VBRJobOptions

In this article

Short Description

Returns job settings.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRJobOptions -Job <CBackupJob[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns job settings for a selected job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the job. The cmdlet will return settings of this job. | Accepts the CBackupJob[] object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | 0 | True (ByProperty Name, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Looking for List of Options of the Specific Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to look for the list of options of the Fileserver Replica job.  |  | | --- | | Get-VBRJob -Name "Fileserver Replica" | Get-VBRJobOptions |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Get-VBRJobOptions cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Looking for List of Options of Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to look for the list of options of the Fileserver Replica job.  |  | | --- | | $fileserver\_replica\_job = Get-VBRJob -Name "Fileserver Replica"  Get-VBRJobOptions -Job $fileserver\_replica\_job |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $fileserver\_replica\_job variable. 2. Run the Get-VBRJobOptions cmdlet. Set the $fileserver\_replica\_job variable as the Job parameter value. |

Related Commands

[Get-VBRJob](get-vbrjob.md)

Page updated 7/16/2025

Page content applies to build 13.0.1.1071
