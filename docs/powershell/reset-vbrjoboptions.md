---
title: "Reset-VBRJobOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/reset-vbrjoboptions.html"
last_updated: "6/11/2024"
product_version: "13.0.1.1071"
---

# Reset-VBRJobOptions

In this article

Short Description

Applies default settings to jobs.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Reset-VBRJobOptions -Job <CBackupJob>  [<CommonParameters>] |

Detailed Description

This cmdlet removes custom settings of a specified job and restores its default values. You can run this cmdlet with any kind of jobs. The VSS settings (application-aware image processing and guest file system indexing) are not reset with this cmdlet.

Run the [Reset-VBRJobVssOptions](reset-vbrjobvssoptions.md) cmdlet to clear the job VSS settings.

Run the [Disable-VBRJobVSSIntegration](disable-vbrjobvssintegration.md) cmdlet or the [Disable-VBRJobGuestFSIndexing](disable-vbrjobguestfsindexing.md) cmdlet to temporarily disable the application-aware image processing and guest file system indexing settings.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the job. The cmdlet will restore default settings of these jobs. | Accepts the CBackupJob object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByProperty Name, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Setting Default Settings to Backup Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to set default settings to backup jobs named Fileserver Backup Job 1 and Fileserver Backup Job 2.  |  | | --- | | Get-VBRJob -Name "Fileserver Backup Job 1", "Fileserver Backup Job 2" | Reset-VBRJobOptions |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Reset-VBRJobOptions cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Setting Default Settings to Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to set default settings to the job.  |  | | --- | | $job = Get-VBRJob -Name "Backup Job"  Reset-VBRJobOptions -Job $job |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Reset-VBRJobOptions cmdlet. Set the $job variable as the Job parameter value. |

Related Commands

[Get-VBRJob](get-vbrjob.md)

Page updated 6/11/2024

Page content applies to build 13.0.1.1071
