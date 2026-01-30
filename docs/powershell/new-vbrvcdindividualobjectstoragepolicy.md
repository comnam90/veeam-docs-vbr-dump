---
title: "New-VBRvCDIndividualObjectStoragePolicy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrvcdindividualobjectstoragepolicy.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# New-VBRvCDIndividualObjectStoragePolicy


Short Description

Defines Cloud Director storage policies for vApps or VMs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Define the vApp storage policies.

|  |
| --- |
| New-VBRvCDIndividualObjectStoragePolicy -VApp <CVcdVappItem> -StoragePolicy <CVcdOrgVdcStorageProfile>  [<CommonParameters>] |

* Define the VM storage policies.

|  |
| --- |
| New-VBRvCDIndividualObjectStoragePolicy -VM <CVcdVappItem> -StoragePolicy <CVcdOrgVdcStorageProfile>  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRvCDIndividualObjectStoragePolicy object. This object defines the settings of Cloud Director storage policies for vApps or VMs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| VApp | Specifies the vApp for which you want to define a storage policy. | Accepts the CVcdVappItem object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | True | Named | False |
| VM | Specifies the VM for which you want to define a storage policy. | Accepts the CVcdVappItem object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | True | Named | False |
| StoragePolicy | Specifies the storage policy. The cmdlet will define a storage policy according to this policy settings. | Accepts the CVcdOrgVdcStorageProfile object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRvCDIndividualObjectStoragePolicy object that defines the settings of Cloud Director storage policies for vApps or VMs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining VApp Storage Policy

|  |  |
| --- | --- |
| This example shows how to define a storage policy for the Atlanta05 vApp.  |  | | --- | | $vapp = Find-VBRvCloudEntity -VApp -Name "Atlanta05"  $policy = Find-VBRvCloudEntity -StorageProfile  $vpolicy = New-VBRvCDIndividualObjectStoragePolicy -VApp $vapp[0] -StoragePolicy $policy[0] |  Perform the following steps:   1. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Specify the Name and VApp parameters. Save the result to the $vapp variable. 2. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Provide the StorageProfile parameter. Save the result to the $policy variable. 3. Run the New-VBRvCDIndividualObjectStoragePolicy cmdlet. Set the $vapp variable as the VApp parameter value. Set the $policy variable as the StoragePolicy parameter value. Save the result to the $vpolicy variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining VM Storage Policy

|  |  |
| --- | --- |
| This example shows how to define a storage policy for the Admin05 VM.  |  | | --- | | $vapp = Find-VBRvCloudEntity -VM -Name "Admin05"  $policy = Find-VBRvCloudEntity -StorageProfile  $vmpolicy = New-VBRvCDIndividualObjectStoragePolicy -VM $vapp[0] -StoragePolicy $policy[0] |  Perform the following steps:   1. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Specify the Name and VM parameters. Save the result to the $vapp variable. 2. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Provide the StorageProfile parameter. Save the result to the $policy variable. 3. Run the New-VBRvCDIndividualObjectStoragePolicy cmdlet. Set the $vapp variable as the VM parameter value. Set the $policy variable as the StoragePolicy parameter value. Save the result to the $vmpolicy variable. |

Related Commands

[Find-VBRvCloudEntity](find-vbrvcloudentity.md)


