---
title: "Get-VBRAzureVirtualNetworkSubnet"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazurevirtualnetworksubnet.html"
last_updated: "12/14/2023"
product_version: "13.0.1.1071"
---

# Get-VBRAzureVirtualNetworkSubnet


Short Description

Returns Microsoft Azure virtual network subnets available for a subscription.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAzureVirtualNetworkSubnet -Network <VBRAzureVirtualNetwork> [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns virtual network subnets available for a Microsoft Azure subscription.

|  |
| --- |
| Important |
| This cmdlet does not support Microsoft Azure accounts with the Azure Service Manager type of a subscription (ASM, also known as a "classic" type subscription). |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Network | Specifies the virtual network. The cmdlet will return subnets of this virtual network. | Accept the [VBRAzureVirtualNetwork](vbrazurevirtualnetwork.md) object. To get this object, run the [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the array of names. The cmdlet will return virtual networks that match the specified names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureNetworkSubnet](vbrazurenetworksubnet.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Virtual Network Subnets Available for Subscription

|  |  |
| --- | --- |
| This example shows how to get all virtual network subnets associated with a subscription.  |  | | --- | | $account = Get-VBRAzureAccount -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  $network = Get-VBRAzureVirtualNetwork -Subscription $subscription -Name "VeeamInternalNetwork"  Get-VBRAzureVirtualNetworkSubnet -Network $network |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Specify the Name parameter value. Save it to the $account variable. 2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save it to the $subscription variable. 3. Run the [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Save it to the $network variable. 4. Run the Get-VBRAzureVirtualNetworkSubnet cmdlet. Set the $network variable as the Network parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Virtual Network Subnet by Name

|  |  |
| --- | --- |
| This example shows how to get a virtual network subnet by the subnet name.  |  | | --- | | $account = Get-VBRAzureAccount -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  $network = Get-VBRAzureVirtualNetwork -Subscription $subscription -Name "VeeamInternalNetwork"  Get-VBRAzureVirtualNetworkSubnet -Network $network -Name "VeeamInternalSubnet" |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Specify the Name parameter value. Save it to the $account variable. 2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save it to the $subscription variable. 3. Run the [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Save it to the $network variable. 4. Run the Get-VBRAzureVirtualNetworkSubnet cmdlet. Set the $network variable as the Network parameter value. Specify the Name parameter value. |

Related Commands

[Get-VBRAzureSubscription](get-vbrazuresubscription.md)


