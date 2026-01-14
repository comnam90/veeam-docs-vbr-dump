---
title: "Get-VBRJobObjectVssOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrjobobjectvssoptions.html"
last_updated: "3/13/2024"
product_version: "13.0.1.1071"
---

# Get-VBRJobObjectVssOptions

In this article

Short Description

Returns VSS settings of a specific VM in job.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRJobObjectVssOptions -ObjectInJob <CObjectInJob>  [<CommonParameters>] |

Detailed Description

This cmdlet returns VSS settings set for a specific VM in job.

Run the [Get-VBRJobVssOptions](get-vbrjobvssoptions.md) cmdlet to get the list of VSS options of a specific job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| ObjectInJob | Specifies the VMs or VM containers for which you want to get VSS options. | Accepts the CObjectInJob object. To get this object, run the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. | True | 0 | True (ByProperty Name, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Looking for VSS Settings of VM Included in Specific Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to look for the VSS settings of the first VM included in the Exchange Backup Copy job.  |  | | --- | | Get-VBRJob -Name "Exchange Backup Copy" | Get-VBRJobObject | Select -First 1 | Get-VBRJobObjectVssOptions |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. 3. Pipe the cmdlet output to the Select. Set the 1 number as the First parameter value. 4. Pipe the cmdlet output to the Get-VBRJobObjectVssOptions cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Looking for VSS Settings of VM [Using Variable]

|  |  |
| --- | --- |
| This example shows how to look for the VSS settings of the VM represented by the $vm variable.  |  | | --- | | $job = Get-VBRJob -Name "Exchange Backup Copy"  $vm = Get-VBRJobObject -Job $job  Get-VBRJobObjectVssOptions -ObjectInJob $vm |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. Set the $job variable as the Job parameter value. Save the result to the $vm variable. 3. Run the Get-VBRJobObjectVssOptions cmdlet. Set the $vm variable as the ObjectInJob parameter value. |

Related Commands

* [Get-VBRJobObject](get-vbrjobobject.md)
* [Get-VBRJob](get-vbrjob.md)

Page updated 3/13/2024

Page content applies to build 13.0.1.1071
