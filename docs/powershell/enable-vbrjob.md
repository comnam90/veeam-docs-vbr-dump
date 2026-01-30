---
title: "Enable-VBRJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrjob.html"
last_updated: "12/16/2025"
product_version: "13.0.1.1071"
---

# Enable-VBRJob


Short Description

Enables a disabled job.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRJob -Job <CBackupJob[]>  [<CommonParameters>] |

Detailed Description

This cmdlet enables a disabled job. When you disable a job, you put it on hold until you enable it with this cmdlet. You can run this cmdlet with backup, replication and tape jobs.

Run the [Enable-VBRBackupCopyJob](enable-vbrbackupcopyjob.md) cmdlet to enable a backup copy job.

Run the [Disable-VBRJob](disable-vbrjob.md) cmdlet to disable a job.

Run the [Start-VBRJob](start-vbrjob.md) cmdlet to start a job once.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of jobs you want to enable. | Accepts the CBackupJob[] object. To get this object, run the [Get-VBRJob](get-vbrjob.md) or [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. | True | Named | True (ByProperty Name, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Enabling Specific Jobs [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to enable the Backup Job 01 and Backup Job 02 jobs.  |  | | --- | | Get-VBRJob -Name "Backup Job 01", "Backup Job 02" | Enable-VBRJob |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Enable-VBRJob cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Enabling Specific Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to enable the job represented by the $job variable.  |  | | --- | | $job = Get-VBRJob -Name "Backup Job"  Enable-VBRJob -Job $job |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Enable-VBRJob cmdlet. Set the $job variable as the Job parameter value. |

Related Commands

[Get-VBRJob](get-vbrjob.md)


