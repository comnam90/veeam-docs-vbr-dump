---
title: "Remove-VBRJobObject"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrjobobject.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRJobObject


Short Description

Removes VMs or VM containers from jobs.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRJobObject -Objects <CObjectInJob[]> [-Completely]  [<CommonParameters>] |

Detailed Description

This cmdlet allows you to remove VMs or VM containers from existing backup, replication or copy job.

You can remove the objects from job completely or only exclude them from processing.

* If you remove the objects completely, they are deleted from job settings and from Veeam database. Run the cmdlet with the Completely parameter for this.
* If you run the cmdlet without the Completely parameter, the job objects are only excluded from processing but remain in job settings.

Note that Veeam PowerShell does not allow you to include the excluded objects back to the job, you can do it only with Veeam Backup & Replication UI.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Objects | Specifies an array of job objects (VMs and VM containers). The cmdlet will exclude these objects from processing by the job.  Note: If the job is processing VM containers, the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet will return only VM containers. To exclude VMs from containers, use Veeam Backup & Replication UI. | Accepts the CObjectInJob[] object. To get this object, run the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. | True | 1 | True (ByProperty Name, ByValue) |
| Completely | If you provide this parameter, you will be able to permanently remove the job objects from the job. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing VM from Backup Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to remove a Fileserver03 VM from the Fileservers Backup Job.  |  | | --- | | Get-VBRJob -Name "Fileservers Backup Job" | Get-VBRJobObject -Name "Fileserver03" | Remove-VBRJobObject  Name             Type       ApproxSize       Location ----             ----       ----------       -------- Fileserver03     Exclude    117.1 GB         tech.tech.local... |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter. 2. Pipe the cmdlet output to the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. Specify the Name parameter value. 3. Pipe the cmdlet output to the Remove-VBRJobObject cmdlet. 4. Run the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet again to check the VM state.   The cmdlet output will contain the following details on the VM state: Name, Type, ApproxSize and the Location. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Completely Removing VM from Backup Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to completely remove a Fileserver03 VM from the Fileservers Backup Job.  |  | | --- | | Get-VBRJob -Name "Fileservers Backup Job" | Get-VBRJobObject -Name "Fileserver03" | Remove-VBRJobObject -Completely |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. Specify the Name parameter value. 3. Pipe the cmdlet output to the Remove-VBRJobObject cmdlet. Provide the Completely parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Removing Specific VMs from Backup Job [Using Variables]

|  |  |
| --- | --- |
| This example shows how to remove Fileserver03 and Fileserver04 VMs from the Fileservers Backup Job.  |  | | --- | | $backupjob = Get-VBRJob -Name "Fileservers Backup Job"  $jobobject = Get-VBRJobObject -Job $backupjob -Name "Fileserver03", "Fileserver04"  Remove-VBRJobObject -Objects $jobobject |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $backupjob variable. 2. Run the [Get-VBRJobObject](get-vbrjobobject.md) cmdlet. Set the $backupjob variable as the Job parameter value. Specify the Name parameter value. Save the result to the $jobobject variable. 3. Run the Remove-VBRJobObject cmdlet. Set the $jobobject variable as the Objects parameter value. |

Related Commands

* [Get-VBRJobObject](get-vbrjobobject.md)
* [Get-VBRJob](get-vbrjob.md)


