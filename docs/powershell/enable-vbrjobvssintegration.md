---
title: "Enable-VBRJobVSSIntegration"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrjobvssintegration.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Enable-VBRJobVSSIntegration

In this article

Short Description

Enables job VSS settings.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRJobVSSIntegration -Job <CBackupJob[]>  [<CommonParameters>] |

Detailed Description

This cmdlet enables VSS settings in a selected job that were previously disabled. You can enable the VSS settings in case you have these settings set beforehand.

You can run this cmdlet with backup and replica jobs including Cloud Director jobs.

Run the [Disable-VBRJobVSSIntegration](disable-vbrjobvssintegration.md) cmdlet to disable VSS settings in the selected job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of jobs. The cmdlet will enable VSS settings for these jobs. | Accepts the CBackupJob[] object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | 0 | True (ByProperty Name, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Enabling VSS Option in Specific Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to enable the VSS option in the Backup Job 01 and Backup Job 02 jobs.  |  | | --- | | Get-VBRJob -Name "Backup Job 01", "Backup Job 02" | Enable-VBRJobVSSIntegration |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Enable-VBRJobVSSIntegration cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Enabling VSS Option in Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to enable the VSS option in the Backup Job 01 job.  |  | | --- | | $BackupJob01 = Get-VBRJob -Name "Backup Job 01"  Enable-VBRJobVSSIntegration -Job $BackupJob01 |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $BackupJob01 variable. 2. Run the Enable-VBRJobVSSIntegration cmdlet. Set the $BackupJob01 variable as the Job parameter value. |

Related Commands

[Get-VBRJob](get-vbrjob.md)

Page updated 4/24/2024

Page content applies to build 13.0.1.1071
