---
title: "Get-VBRJobObject"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrjobobject.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# Get-VBRJobObject


Short Description

Returns VMs or VM containers of specific jobs.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRJobObject -Job <CBackupJob> [-Name <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns the following VMs or VM containers of specific jobs:

* VMs
* VM containers
* Datastores
* Resource pools

You can run this cmdlet for backup, replication, VM copy or file copy jobs.

|  |
| --- |
| Note |
| The cmdlet returns only the objects added to a job. For example, if you have added datastores, the cmdlet will return these datastores. The cmdlet will not return VMs from these datastores. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the job. The cmdlet will return objects of this job. | Accepts the CBackupJob object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | 0 | True (ByProperty Name, ByValue) |
| Name | Specifies the array of job object names (for example, VMs). The cmdlet will filter the objects of the job by these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CObjectInJob object that contains objects of a job.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Looking for VM in Specific Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to look for the SharePoint VM in the VM Copy Job 01 job.  |  | | --- | | Get-VBRJob -Name "VM Copy Job 01" | Get-VBRJobObject -Name \*SharePoint\* |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Get-VBRJobObject cmdlet. Specify the Name parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Looking for VM in Specific Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to look for the SharePoint VM in the job represented by the $job variable.  |  | | --- | | $job = Get-VBRJob  Get-VBRJobObject -Job $job -Name "SharePoint" |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Save the result to the $job variable. 2. Run the Get-VBRJobObject cmdlet. Set the $job variable as the Job parameter value. Specify the Name parameter. |

Related Commands

[Get-VBRJob](get-vbrjob.md)


