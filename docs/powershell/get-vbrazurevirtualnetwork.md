---
title: "Get-VBRAzureVirtualNetwork"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazurevirtualnetwork.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Get-VBRAzureVirtualNetwork


Short Description

Returns Microsoft Azure virtual networks available for a subscription.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAzureVirtualNetwork -Subscription <VBRAzureSubscription> [-Name <string[]>] [-Location <VBRAzureLocation>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns virtual networks available for a Microsoft Azure subscription.

|  |
| --- |
| Important |
| This cmdlet does not support Microsoft Azure accounts with the Azure Service Manager type of a subscription (ASM, also known as a "classic" type subscription). |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Subscription | Specifies a subscription. The cmdlet will return virtual networks associated with this subscription. | Accepts the [VBRAzureSubscription](vbrazuresubscription.md) object. To get this object, run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Name | Specifies an array of names. The cmdlet will return virtual networks that match the specified names. | String[] | False | Named | False |
| Location | Specifies geographic locations of Microsoft Azure datacenters available for the virtual network. | Accepts the [VBRAzureLocation](vbrazurelocation.md) object. To get this object, run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureVirtualNetwork](vbrazurevirtualnetwork.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Virtual Networks Available for Subscription

|  |  |
| --- | --- |
| This example shows how to get all virtual networks associated with a subscription.  |  | | --- | | $account = Get-VBRAzureAccount -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  Get-VBRAzureVirtualNetwork -Subscription $subscription |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Specify the Name parameter value. Save it to the $account variable. 2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save it to the $subscription variable. 3. Run the Get-VBRAzureVirtualNetwork cmdlet. Set the $subscription variable as the Subscription parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Virtual Network by Name

|  |  |
| --- | --- |
| This example shows how to get a virtual network by the virtual network name.  |  | | --- | | $account = Get-VBRAzureAccount -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  Get-VBRAzureVirtualNetwork -Subscription $subscription -Name "VeeamInternalNetwork" |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Specify the Name parameter value. Save it to the $account variable. 2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save it to the $subscription variable. 3. Run the Get-VBRAzureVirtualNetwork cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. |

Related Commands

[Get-VBRAzureSubscription](get-vbrazuresubscription.md)


