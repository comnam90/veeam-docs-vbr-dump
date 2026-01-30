---
title: "Get-VBRJobVssOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrjobvssoptions.html"
last_updated: "3/13/2024"
product_version: "13.0.1.1071"
---

# Get-VBRJobVssOptions


Short Description

Returns VSS settings for a selected job.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRJobVSSOptions -Job <CBackupJob[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns VSS settings for a selected job.

Run the [Get-VBRJobObjectVssOptions](get-vbrjobobjectvssoptions.md) cmdlet to get the list of VSS options set for specific objects in a job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the job you want to get the VSS options of. | Accepts the CBackupJob object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | 0 | True (ByProperty Name, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Looking for List of VSS Options of Specific Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to look for the list of VSS options of the ActiveDirectory Backup job.  |  | | --- | | Get-VBRJob -Name "ActiveDirectory Backup" | Get-VBRJobVSSOptions |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Get-VBRJobVSSOptions cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Looking for List of Options of Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to look for the list of options of the job represented by the $ad\_backup variable.  |  | | --- | | $ad\_backup = Get-VBRJob -Name "ActiveDirectory Backup"  Get-VBRJobVSSOptions -Job $ad\_backup |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $ad\_backup variable. 2. Run the Get-VBRJobVSSOptions cmdlet. Set the $ad\_backup variable as the Job parameter value. |

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Get-VBRJobObject](get-vbrjobobject.md)


