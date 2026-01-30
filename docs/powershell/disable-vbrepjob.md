---
title: "Disable-VBREPJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrepjob.html"
last_updated: "2/7/2025"
product_version: "13.0.1.1071"
---

# Disable-VBREPJob


Short Description

Disables backup jobs run by Veeam Agent operating in the standalone mode.

Syntax

|  |
| --- |
| Disable-VBREPJob -Job <VBREPJob[]>  [<CommonParameters>] |

Detailed Description

This cmdlet disables backup jobs run by Veeam Agent operating in the standalone mode.

When you disable a job, you temporarily put it on hold. The job and its settings are not deleted from Veeam Backup & Replication.

Run the [Enable-VBREPJob](enable-vbrepjob.md) cmdlet to enable a disabled job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of backup jobs. The cmdlet will disable these jobs. | Accepts the [VBREPJob](vbrepjob.md) object. To get this object, run the [Get-VBREPJob](get-vbrepjob.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBREPJob](vbrepjob.md)[]

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Disabling Backup Job Run by Veeam Agent in Standalone Mode [Using Variable]

|  |  |
| --- | --- |
| This example shows how to disable a backup job run by Veeam Agent operating in the standalone mode using a variable.  |  | | --- | | $job = Get-VBREPJob -Name "Backup Job Mediaserver"  Disable-VBREPJob -Job $job |  Perform the following steps:   1. Run the [Get-VBREPJob](get-vbrepjob.md) cmdlet. Specify the Name parameter value. Save it to the $job variable. 2. Run the Disable-VBREPJob cmdlet. Set the $job variable as the Job parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Disabling Backup Job Run by Veeam Agent in Standalone Mode [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to disable a backup job run by Veeam Agent operating in the standalone mode using a pipeline.  |  | | --- | | Get-VBREPJob -Name "Backup Job Mediaserver" | Disable-VBREPJob |  Perform the following steps:   1. Run the [Get-VBREPJob](get-vbrepjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Disable-VBREPJob cmdlet. |

Related Commands

[Get-VBREPJob](get-vbrepjob.md)


