---
title: "Add-VBRVMExclusion"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrvmexclusion.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Add-VBRVMExclusion


Short Description

Adds VMs to global VM exclusions.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRVMExclusion -Entity <Object[]> [-Note <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet adds VMs to global VM exclusions. Veeam Backup & Replication stops processing such VMs even if they are included in jobs.

|  |
| --- |
| Note |
| Global VM exclusion applies only to jobs where the sources are production VMs. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Entity | Specifies the VMs which you want to exclude from processing. | Accepts the Object[] object. To get this object, run the following cmdlets:   * [Find-VBRViEntity](find-vbrvientity.md): use this cmdlet to get VMware vSphere VMs. * [Find-VBRHvEntity](find-vbrhventity.md): use this cmdlet to get Microsoft Hyper-V VMs. * [Find-VBRvCloudEntity](find-vbrvcloudentity.md): use this cmdlet to get Cloud Director VMs. | True | 0 | True (ByPropertyName, ByValue) |
| Note | Specifies a note why the VM is excluded from processing. | String | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRVMExclusion[] object that defines the exclusions.

Examples

Excluding VMware vSphere VM from Processing

This example shows how to exclude the ubuntu88 VMware vSphere VM from processing.

|  |
| --- |
| $vm = Find-VBRViEntity -VMsAndTemplates -Name "ubuntu88"  Add-VBRVMExclusion -Entity $vm |

Perform the following steps:

1. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Provide the VMsAndTemplates parameter. Specify the Name parameter value. Save the result to the $vm variable.
2. Run the Add-VBRVMExclusion cmdlet. Set the $vm variable as the Entity parameter value.


