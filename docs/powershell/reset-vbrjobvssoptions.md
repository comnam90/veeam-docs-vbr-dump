---
title: "Reset-VBRJobVssOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/reset-vbrjobvssoptions.html"
last_updated: "3/13/2024"
product_version: "13.0.1.1071"
---

# Reset-VBRJobVssOptions


Short Description

Sets job VSS settings to default.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Reset-VBRJobVssOptions -Job <CBackupJob>  [<CommonParameters>] |

Detailed Description

This cmdlet clears the custom VSS settings of the specified job and restores their default values.

You can run this cmdlet with any kind of jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the job you want to edit. | Accepts the CBackupJob object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByProperty Name, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Setting Default VSS Settings to Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to set default VSS settings to Fileserver Backup Job 1 and Fileserver Backup Job 2 backup jobs.  |  | | --- | | Get-VBRJob -Name "Fileserver Backup Job 1", "Fileserver Backup Job 2" | Reset-VBRJobVssOptions |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Reset-VBRJobVssOptions cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Setting Default VSS Settings to Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to set default VSS settings to the job represented by the $job variable.  |  | | --- | | $job = Get-VBRJob -Name "Fileserver Backup Job 1"  Reset-VBRJobVssOptions -Job $job |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Reset-VBRJobVssOptions cmdlet. Set the $job variable as the Job parameter value. |

Related Commands

[Get-VBRJob](get-vbrjob.md)


