---
title: "Add-VBRvCloudJobObject"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrvcloudjobobject.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Add-VBRvCloudJobObject


Short Description

Adds VMs to Cloud Director backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRvCloudJobObject -Entities <IVcdItem[]> [-Force] -Job <CBackupJob>  [<CommonParameters>] |

Detailed Description

This cmdlet adds VMs to Cloud Director backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies a Cloud Director backup job. The cmdlet will add VMs to this Cloud Director backup job. | Accepts the CBackupJob object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | False |
| Entities | Specifies an array of VMs that you want to add to a Cloud Director backup job. | Accepts the IVcdItem[] object. To create this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Force | Defines that the cmdlet will add VMs to a Cloud Director backup job without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRvCloudJobObject object that contains settings of VMs to Cloud Director backup job.

Examples

Adding VMs to Cloud Director Backup Job

This example shows how to add the WinSrv2907 VM to the Cloud backup job Cloud Director backup job.

|  |
| --- |
| $job = Get-VBRJob -Name "Cloud backup job"  $vm = Find-VBRvCloudEntity -Name "WinSrv2907"  Add-VBRvCloudJobObject -Job $job -Entities $vm |

Perform the following steps:

1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Specify the Name parameter value. Save the result to the $vm variable.
3. Run the Add-VBRvCloudJobObject cmdlet. Set the $job variable as the Job parameter value. Set the $vm variable as the Entities parameter value.

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Find-VBRvCloudEntity](find-vbrvcloudentity.md)


