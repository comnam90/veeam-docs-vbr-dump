---
title: "Add-VBRHvJobObject"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrhvjobobject.html"
last_updated: "6/11/2024"
product_version: "13.0.1.1071"
---

# Add-VBRHvJobObject


Short Description

Adds VMs to Hyper-V jobs.

Applies to

Platform: Hyper-V

For VMware, run the [Add-VBRViJobObject](add-vbrvijobobject.md) cmdlet.

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRHvJobObject -Entities <IHvItem[]> [-Force] -Job <CBackupJob>  [<CommonParameters>] |

Detailed Description

This cmdlet adds VMs to Hyper-V jobs.

You can run this cmdlet with any kind of jobs.

|  |
| --- |
| ![Add-VBRHvJobObject](images/icon_note.webp) Note: |
| The cmdlet will not run if the geographic location of the VMs added to the job and the job target repository location do not match. If you still want to run the cmdlet, use the Force parameter. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the job. The cmdlet will add VMs to this job. | Accepts the CBackupJob object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | False |
| Entities | Specifies the array of Hyper-V VMs you want to add to the job. | Accepts the IHvItem[] object. To get this object, run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. | True | Named | True (ByProperty Name, ByValue) |
| Force | Defines that the cmdlet will add VMs to the existing job even if the geographic location of these VMs and the target backup repository location do not match. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding VM to Job Represented by Variable [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to add a VM named VM01 to the job represented by the $BackupHVJob variable.  |  | | --- | | $BackupHvJob = Get-VBRJob -Name "Backup Job"  Find-VBRHvEntity -Name VM01 | Add-VBRHvJobObject -Job $BackupHvJob |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $BackupHvJob variable. 2. Run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. Specify the Name parameter value. 3. Pipe the cmdlet output to the Add-VBRHvJobObject cmdlet. Set the $BackupHvJob variable as the Job parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding VM to Specific Job [Using Variables]

|  |  |
| --- | --- |
| This example shows how to add a VM represented by $Vm variable to the job represented by $BackupHvJob variable.  |  | | --- | | $BackupHvJob = Get-VBRJob -Name "Backup Job"  $Vm = Find-VBRHvEntity -Name "VM01"  Add-VBRHvJobObject -Job $BackupHvJob -Entities $Vm |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $BackupHvJob variable. 2. Run the [Find-VBRHvEntity](find-vbrhventity.md) cmdlet. Specify the Name parameter value. Save the result to the $Vm variable. 3. Run the Add-VBRHvJobObject cmdlet. Set the $BackupHvJob variable as the Job parameter value. Set the $Vm variable as the Entities parameter value. |

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Find-VBRHvEntity](find-vbrhventity.md)


