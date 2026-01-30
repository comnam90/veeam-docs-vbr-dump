---
title: "New-VBRAzureLinuxRestoreAppliance"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrazurelinuxrestoreappliance.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# New-VBRAzureLinuxRestoreAppliance


Short Description

Creates helper appliances for restoring Linux VMs to Microsoft Azure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRAzureLinuxRestoreAppliance -Subscription <VBRAzureSubscription> -StorageAccount <VBRAzureStorageAccount> -VirtualNetwork <VBRAzureVirtualNetwork> -VirtualSubnet <VBRAzureNetworkSubnet> [-ResourceGroup <VBRAzureResourceGroup>] [-SshPort <Int32>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a helper appliance for restoring Linux VMs to Microsoft Azure.

You will need to further deploy the helper appliance with the [Deploy-VBRAzureLinuxRestoreAppliance](deploy-vbrazurelinuxrestoreappliance.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Subscription | Specifies the Microsoft Azure subscription in which you plan to deploy the helper appliance. | Accepts the [VBRAzureSubscription](vbrazuresubscription.md) object. To create this object, run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| StorageAccount | Specifies the storage account you want to use to deploy the helper appliance. | Accepts the [VBRAzureStorageAccount](vbrazurestorageaccount.md) object. To create this object, run the [Get-VBRAzureStorageAccount](get-vbrazurestorageaccount.md) cmdlet. | True | Named | True (ByProperty Name) |
| VirtualNetwork | Specifies the virtual network to which you want to connect the helper appliance. | Accepts the [VBRAzureVirtualNetwork](vbrazurevirtualnetwork.md) object. To create this object, run the [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md) cmdlet. | True | Named | True (ByProperty Name) |
| VirtualSubnet | Specifies the virtual network subnet to which you want to connect the helper appliance. | Accepts the [VBRAzureNetworkSubnet](vbrazurenetworksubnet.md) object. To create this object, run the [Get-VBRAzureVirtualNetworkSubnet](get-vbrazurevirtualnetworksubnet.md) cmdlet. | True | Named | True (ByProperty Name) |
| ResourceGroup | Specifies the resource group to which you want to connect the helper appliance. | Accepts the [VBRAzureResourceGroup](vbrazureresourcegroup.md) object. To create this object, run the [Get-VBRAzureResourceGroup](get-vbrazureresourcegroup.md) cmdlet. | False | Named | True (ByProperty Name) |
| SshPort | Specifies the port that used to connect the helper appliance. | Int32 | False | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureLinuxRestoreAppliance](vbrazurelinuxrestoreappliance.md)

Examples

Restoring VM to Resource Manager Account

This example shows how to restore a VM to a Resource Manager account.

|  |
| --- |
| $account = Get-VBRAzureAccount -Type ResourceManager -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  $storageaccount = Get-VBRAzureStorageAccount -Subscription $subscription -Name "VeeamDirectRestore2AzureStorage"  $network = Get-VBRAzureVirtualNetwork -Subscription $subscription -Name "VeeamInternalNetwork"  $subnet = Get-VBRAzureVirtualNetworkSubnet -Network $network -Name "VeeamInternalSubnet"  New-VBRAzureLinuxRestoreAppliance -Subscription $subscription -StorageAccount $storageaccount -VirtualNetwork $network -VirtualSubnet $subnet |

Perform the following steps:

1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Set the ResourceManager value as the Type parameter value. Specify the Name parameter value. Save it to the $account variable.
2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save it to the $subscription variable.
3. Run the [Get-VBRAzureStorageAccount](get-vbrazurestorageaccount.md) cmdlet.  Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Save it to the $storageaccount variable.
4. Run the [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Save the result to the $network variable.
5. Run the [Get-VBRAzureVirtualNetworkSubnet](get-vbrazurevirtualnetworksubnet.md) cmdlet. Set the $network variable as the Network parameter value. Specify the Name parameter value. Save the result to the $subnet variable.
6. Run the New-VBRAzureLinuxRestoreAppliance cmdlet. Specify the following settings:

* Set the $subscription variable as the Subscription parameter value.
* Set the $storageaccount variable as the StorageAccount parameter value.
* Set the $network variable as the VirtualNetwork parameter value.
* Set the $subnet variable as the VirtualSubnet parameter value.

Related Commands

* [Get-VBRAzureSubscription](get-vbrazuresubscription.md)
* [Get-VBRAzureStorageAccount](get-vbrazurestorageaccount.md)
* [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md)
* [VBRAzureNetworkSubnet](vbrazurenetworksubnet.md)


