---
title: "Disable-VBRJobVSSIntegration"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrjobvssintegration.html"
last_updated: "6/12/2024"
product_version: "13.0.1.1071"
---

# Disable-VBRJobVSSIntegration

In this article

Short Description

Disables job VSS settings.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRJobVSSIntegration -Job <CBackupJob[]>  [<CommonParameters>] |

Detailed Description

This cmdlet disables the VSS settings in the selected job. The VSS settings are not deleted form the job.

You can run this cmdlet with backup and replication jobs.

Run the [Enable-VBRJobVSSIntegration](enable-vbrjobvssintegration.md) cmdlet to enable VSS settings in the selected job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of jobs. The cmdlet will disable VSS settings for these jobs. | Accepts the CBackupJob object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | 0 | True (ByProperty Name, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Disabling VSS Options in Specific Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to disable the VSS options in the Backup Job 01 and Backup Job 02 jobs.  |  | | --- | | Get-VBRJob -Name "Backup Job 01", "Backup Job 02" | Disable-VBRJobVSSIntegration |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Disable-VBRJobVSSIntegration cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Disabling VSS Options in Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to disable the VSS options in job represented by the $job variable.  |  | | --- | | $job = Get-VBRJob -Name "Backup Job 02"  Disable-VBRJobVSSIntegration -Job $job |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Disable-VBRJobVSSIntegration cmdlet. Set the $job variable as the Job parameter value. |

Related Commands

[Get-VBRJob](get-vbrjob.md)

Page updated 6/12/2024

Page content applies to build 13.0.1.1071
