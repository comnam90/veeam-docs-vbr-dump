---
title: "Set-VBRAzureLinuxRestoreAppliance"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrazurelinuxrestoreappliance.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Set-VBRAzureLinuxRestoreAppliance


Short Description

Modifies helper appliances for restoring Linux VMs to Microsoft Azure.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRAzureLinuxRestoreAppliance -Appliance <VBRAzureLinuxRestoreAppliance> [-Subscription <VBRAzureSubscription>] [-StorageAccount <VBRAzureStorageAccount>] [-ResourceGroup <VBRAzureResourceGroup>][-VirtualNetwork <VBRAzureVirtualNetwork>] [-VirtualSubnet <VBRAzureNetworkSubnet>] [-SshPort <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies helper appliances for restoring Linux VMs to Microsoft Azure.

You will need to further deploy the helper appliance with the [Deploy-VBRAzureLinuxRestoreAppliance](deploy-vbrazurelinuxrestoreappliance.md) cmdlet.

|  |
| --- |
| Important |
| This cmdlet does not support Microsoft Azure accounts with the Azure Service Manager type of a subscription (ASM, also known as a "classic" type subscription). |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Appliance | Specifies the helper appliance you want to modify. | Accepts the [VBRAzureLinuxRestoreAppliance](vbrazurelinuxrestoreappliance.md) object. To get this object, run the [Get-VBRAzureLinuxRestoreAppliance](get-vbrazurelinuxrestoreappliance.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Subscription | Specifies the Microsoft Azure subscription in which you plan to deploy the helper appliance. | Accepts the [VBRAzureSubscription](vbrazuresubscription.md) object. To get this object, run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. | False | Named | True (ByPropertyName) |
| StorageAccount | Specifies the storage account you want to use to deploy the helper appliance. | Accepts the [VBRAzureStorageAccount](vbrazurestorageaccount.md) object. To get this object, run the [Get-VBRAzureStorageAccount](get-vbrazurestorageaccount.md) cmdlet. | False | Named | True (ByPropertyName) |
| ResourceGroup | Specifies a Microsoft Azure resource group to which you want to connect the helper appliance. | Accepts the VBRAzureResourceGroup object. To get this object, run the [Get-VBRAzureResourceGroup](get-vbrazureresourcegroup.md) cmdlet. | False | Named | True (ByPropertyName) |
| VirtualNetwork | Specifies the virtual network to which you want to connect the helper appliance. | Accepts the [VBRAzureVirtualNetwork](vbrazurevirtualnetwork.md) object. To get this object, run the [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md) cmdlet. | False | Named | True (ByPropertyName) |
| VirtualSubnet | Specifies the virtual network subnet to which you want to connect the helper appliance. | Accepts the [VBRAzureNetworkSubnet](vbrazurenetworksubnet.md) object. To get this object, run the [Get-VBRAzureVirtualNetworkSubnet](get-vbrazurevirtualnetworksubnet.md) cmdlet. | False | Named | True (ByPropertyName) |
| SshPort | Specifies a port over which Veeam Backup & Replication will will communicate with the helper appliance. | Int | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureLinuxRestoreAppliance](vbrazurelinuxrestoreappliance.md)

Examples

Setting Storage Account for Linux VM Restore Helper Appliance

This example shows how to set another storage account for a Linux VM restore helper appliance.

|  |
| --- |
| $account = Get-VBRAzureAccount -Type ResourceManager -Name "RestoreToAzureRM@Veeam.com"  $appliance = Get-VBRAzureLinuxRestoreAppliance -Account $account | Select-Object -First 1  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  $newstorageaccount = Get-VBRAzureStorageAccount -Subscription $subscription -Name "VeeamDirectRestore2AzureStorage"  Set-VBRAzureLinuxRestoreAppliance -Appliance $appliance -StorageAccount $newstorageaccount |

Perform the following steps:

1. Get the Linux helper appliance:

* Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Set the ResourceManager option for the Type parameter. Specify the Name parameter value. Save the result to the $account variable.
* Run the [Get-VBRAzureLinuxRestoreAppliance](get-vbrazurelinuxrestoreappliance.md) cmdlet. Set the $account variable as the Account parameter value. Pipe the cmdlet output to the Select-Object cmdlet. Specify the First parameter value. Save the result to the $appliance variable.

1. Get the Microsoft Azure storage account you want to use:

* Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save the subscription to the $subscription variable.
* Run the [Get-VBRAzureStorageAccount](get-vbrazurestorageaccount.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Save it to the $newstorageaccount variable.

1. Run the Set-VBRAzureLinuxRestoreAppliance cmdlet. Set the $appliance variable as the Appliance parameter value. Set the $storageaccount variable as the StorageAccount parameter value.

Related Commands

* [Get-VBRAzureLinuxRestoreAppliance](get-vbrazurelinuxrestoreappliance.md)
* [Get-VBRAzureSubscription](get-vbrazuresubscription.md)
* [Get-VBRAzureStorageAccount](get-vbrazurestorageaccount.md)
* [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md)
* [VBRAzureNetworkSubnet](vbrazurenetworksubnet.md)


