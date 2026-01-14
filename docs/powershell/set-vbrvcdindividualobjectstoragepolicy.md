---
title: "Set-VBRvCDIndividualObjectStoragePolicy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvcdindividualobjectstoragepolicy.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# Set-VBRvCDIndividualObjectStoragePolicy

In this article

Short Description

Modifying the Cloud Director storage policies for vApps or VMs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify the vApp storage policies.

|  |
| --- |
| Set-VBRvCDIndividualObjectStoragePolicy -Policy <VBRvCDIndividualObjectStoragePolicy> [-VApp <CVcdVappItem>] [-StoragePolicy <CVcdOrgVdcStorageProfile>]  [<CommonParameters>] |

* Modify the VM storage policies.

|  |
| --- |
| Set-VBRvCDIndividualObjectStoragePolicy -Policy <VBRvCDIndividualObjectStoragePolicy> [-VM <CVcdVappItem>] [-StoragePolicy <CVcdOrgVdcStorageProfile>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the Cloud Director storage policies for vApps or VMs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Policy | Specifies the  Cloud Director storage policies for vApps or VMs. The cmdlet will modify this policy. | Accepts the VBRvCDIndividualObjectStoragePolicy object. To create this object, run the [New-VBRvCDIndividualObjectStoragePolicy](new-vbrvcdindividualobjectstoragepolicy.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| VApp | Specifies the vApp for which you want to modify a storage policy. | Accepts the CVcdVappItem object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| VM | Specifies the VM for which you want to modify a storage policy. | Accepts the CVcdVappItem object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |
| StoragePolicy | Specifies the storage policy. The cmdlet will modify a storage policy according to this policy settings. | Accepts the CVcdOrgVdcStorageProfile object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRvCDIndividualObjectStoragePolicy object that defines the settings of Cloud Director storage policies for vApps or VMs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying VApp Storage Policy

|  |  |
| --- | --- |
| This example shows how to apply the Virginia vApp policy for the Atlanta05 policy.  |  | | --- | | $vapp = Find-VBRvCloudEntity -VApp -Name "Atlanta05"  $policy = Find-VBRvCloudEntity -StorageProfile  $vpolicy = New-VBRvCDIndividualObjectStoragePolicy -VApp $vapp[0] -StoragePolicy $policy[0]  $newpolicy = Find-VBRvCloudEntity -StorageProfile -Name "Virginia vApp"  Set-VBRvCDIndividualObjectStoragePolicy -Policy $vpolicy -StoragePolicy $newpolicy |  Perform the following steps:   1. Define the settings of Cloud Director storage policies for vApps.  1. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Specify the Name and VApp parameters. Save the result to the $vapp variable. 2. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Provide the StorageProfile parameter. Save the result to the $policy variable. 3. Run the [New-VBRvCDIndividualObjectStoragePolicy](new-vbrvcdindividualobjectstoragepolicy.md) cmdlet. Specify the VApp and the StoragePolicy parameters. Save the result to the $vpolicy variable.  1. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Specify the StoragePolicy and the Name parameters. Save the result to the $newpolicy variable. 2. Run the Set-VBRvCDIndividualObjectStoragePolicy cmdlet. Set the $vpolicy variable as the Policy parameter value. Set the $newpolicy variable as the StoragePolicy parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying VM Storage Policy

|  |  |
| --- | --- |
| This example shows how to apply the Virginia vApp policy for the Admin05 VM.  |  | | --- | | $vapp = Find-VBRvCloudEntity -VM -Name "Admin05"  $policy = Find-VBRvCloudEntity -StorageProfile  $vmpolicy = New-VBRvCDIndividualObjectStoragePolicy -VM $vapp[0] -StoragePolicy $policy[0]  $newpolicy = Find-VBRvCloudEntity -StorageProfile -Name "Virginia vApp"  Set-VBRvCDIndividualObjectStoragePolicy -Policy $vmpolicy -StoragePolicy $newpolicy |  Perform the following steps:   1. Define the settings of Cloud Director storage policies for vApps.  1. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Specify the Name and VApp parameters. Save the result to the $vapp variable. 2. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Provide the StorageProfile parameter. Save the result to the $policy variable. 3. Run the [New-VBRvCDIndividualObjectStoragePolicy](new-vbrvcdindividualobjectstoragepolicy.md) cmdlet. Specify the VM and the StoragePolicy parameters. Save the result to the $vmpolicy variable.  1. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Specify the StoragePolicy and the Name parameters. Save the result to the $newpolicy variable. 2. Run the Set-VBRvCDIndividualObjectStoragePolicy cmdlet. Set the $vmpolicy variable as the Policy parameter value. Set the $newpolicy variable as the StoragePolicy parameter value. |

Related Commands

* [Find-VBRvCloudEntity](find-vbrvcloudentity.md)
* [New-VBRvCDIndividualObjectStoragePolicy](new-vbrvcdindividualobjectstoragepolicy.md)

Page updated 1/28/2025

Page content applies to build 13.0.1.1071
