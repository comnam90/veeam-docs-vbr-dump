---
title: "Disable-VBRJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrjob.html"
last_updated: "12/16/2025"
product_version: "13.0.1.1071"
---

# Disable-VBRJob

In this article

Short Description

Puts a selected job on hold.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRJob -Job <CBackupJob[]>  [<CommonParameters>] |

Detailed Description

This cmdlet disables an enabled job. The job and its settings are not deleted from Veeam Backup & Replication. You can run this cmdlet with backup, replication and tape jobs.

Run the [Disable-VBRBackupCopyJob](disable-vbrbackupcopyjob.md) cmdlet to disable a backup copy job.

Run the [Enable-VBRJob](enable-vbrjob.md) cmdlet to enable the job.

Run the [Stop-VBRJob](stop-vbrjob.md) cmdlet to stop the job once without disabling it.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of jobs you want to disable. | Accepts the CBackupJob object. To get this object, run the [Get-VBRJob](get-vbrjob.md) or [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. | True | Named | True (ByProperty Name, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Disabling Specific Jobs [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to disable jobs named Backup Job 01 and Backup Job 02.  |  | | --- | | Get-VBRJob -Name "Backup Job 01", "Backup Job 02" | Disable-VBRJob |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Disable-VBRJob cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Disabling Specific Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to disable the job represented by the $job variable.  |  | | --- | | $job = Get-VBRJob -Name "Backup Job"  Disable-VBRJob -Job $job |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Disable-VBRJob cmdlet. Set the $job variable as the Job parameter value. |

Related Commands

[Get-VBRJob](get-vbrjob.md)

Page updated 12/16/2025

Page content applies to build 13.0.1.1071
