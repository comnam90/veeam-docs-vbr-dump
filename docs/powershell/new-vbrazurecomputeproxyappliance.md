---
title: "New-VBRAzureComputeProxyAppliance"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrazurecomputeproxyappliance.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# New-VBRAzureComputeProxyAppliance

In this article

Short Description

Defines proxy appliance settings for adding Azure Archive repository.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRAzureComputeProxyAppliance -VMSize <VBRAzureVMSize> -Network <VBRAzureVirtualNetwork> -Subnet <VBRAzureNetworkSubnet> -ResourceGroup <VBRAzureResourceGroup> [-RedirectorPort <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet defines the proxy appliance settings for adding an Azure Archive repository.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| VMSize | Specifies the size of the proxy appliance. | Accepts the VBRAzureVMSize object. To create this object, run the [Get-VBRAzureVMSize](get-vbrazurevmsize.md) cmdlet. | True | Named | False |
| Network | Specifies the network to which the proxy appliance appliance must be connected. | Accepts the VBRAzureVirtualNetwork object. To create this object, run the [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md) cmdlet. | True | Named | False |
| Subnet | Specifies the subnet for the proxy appliance. | Accepts the VBRAzureNetworkSubnet object. To create this object, run the [Get-VBRAzureVirtualNetworkSubnet](get-vbrazurevirtualnetworksubnet.md) cmdlet. | True | Named | False |
| ResourceGroup | Specifies the resource group that will be associated with the proxy appliance. | Accepts the VBRAzureResourceGroup object. To create this object, run the [Get-VBRAzureResourceGroup](get-vbrazureresourcegroup.md) cmdlet. | True | Named | False |
| RedirectorPort | Specifies the port that Veeam Backup & Replication will use to route requests between the proxy appliance and backup infrastructure components. | Int | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureComputeProxyAppliance](vbrazurecomputeproxyappliance.md)

Examples

Adding Azure Proxy Appliance

This example shows how to defines settings of an Azure proxy appliance.

|  |
| --- |
| $account = Get-VBRAzureBlobAccount -Name "Azure\_Blob"  $subscription = Get-VBRAzureSubscription -Account $account  $location = Get-VBRAzureLocation -Subscription $subscription  $vmsize = Get-VBRAzureVMSize -Subscription $subscription -Location $location  $network = Get-VBRAzureVirtualNetwork -Name "VeeamInternalNetwork"  $subnet = Get-VBRAzureVirtualNetworkSubnet -Network $network -Name "VeeamInternalSubnet"  $rg = Get-VBRAzureResourceGroup -Subscription $subscription -Name "VeeamResourceGroup"  New-VBRAzureComputeProxyAppliance -VMSize $vmsize -Network $network -Subnet $subnet -ResourceGroup $rg -RedirectorPort 443 |

Perform the following steps:

1. Run the [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md) cmdlet. Specify the Name parameter value. Save the result to the $account variable.
2. Define the Azure proxy settings:

1. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Save the result to the $subscription variable.
2. Run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Save the result to the $location variable.
3. Run the [Get-VBRAzureVMSize](get-vbrazurevmsize.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Set the $location variable as the Location parameter value. Save the result to the $vmsize variable.
4. Run the [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md) cmdlet. Specify the Name parameter value. Save the result to the $network variable.
5. Run the [Get-VBRAzureVirtualNetworkSubnet](get-vbrazurevirtualnetworksubnet.md) cmdlet. Set the $network variable as the Network parameter value. Specify the Name parameter value. Save the result to the $subnet variable.
6. Run the [Get-VBRAzureResourceGroup](get-vbrazureresourcegroup.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Save the result to the $rg variable.

1. Run the New-VBRAzureComputeProxyAppliance cmdlet. Specify the following settings:

* Set the $vmsize variable as the VMSize parameter value.
* Set the $network variable as the Network parameter value.
* Set the $subnet variable as the Subnet parameter value.
* Set the $rg variable as the ResourceGroup parameter value.
* Specify the RedirectorPort parameter value.

Related Commands

* [Add-VBRAzureArchiveRepository](add-vbrazurearchiverepository.md)
* [Get-VBRAzureBlobAccount](get-vbrazureblobaccount.md)

* [Get-VBRAzureLocation](get-vbrazurelocation.md)
* [Get-VBRAzureVMSize](get-vbrazurevmsize.md)
* [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md)
* [Get-VBRAzureVirtualNetworkSubnet](get-vbrazurevirtualnetworksubnet.md)
* [Get-VBRAzureResourceGroup](get-vbrazureresourcegroup.md)

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
