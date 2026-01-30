---
title: "Get-VBRAzureLocation"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazurelocation.html"
last_updated: "2/20/2024"
product_version: "13.0.1.1071"
---

# Get-VBRAzureLocation


Short Description

Returns geographic locations of Microsoft Azure datacenters available for a subscription.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAzureLocation -Subscription <VBRAzureSubscription> [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns geographic locations of Microsoft Azure datacenters available for a selected subscription.

|  |
| --- |
| Important |
| This cmdlet does not support Microsoft Azure accounts with the Azure Service Manager type of a subscription (ASM, also known as a "classic" type subscription). |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Subscription | Specifies the subscription. The cmdlet will return locations available for this subscription. | Accepts the [VBRAzureSubscription](vbrazuresubscription.md) object. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) to get this object. | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the array of names. The cmdlet will return locations that match the specified names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureLocation](vbrazurelocation.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Locations Available for Subscription

|  |  |
| --- | --- |
| This example shows how to get all locations associated with a subscription.  |  | | --- | | $account = Get-VBRAzureAccount -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  Get-VBRAzureLocation -Subscription $subscription |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Specify the Name parameter value. Save it to the $account variable. 2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save it to the $subscription variable. 3. Run the Get-VBRAzureLocation cmdlet. Set the $subscription variable as the Subscription parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Location by Name

|  |  |
| --- | --- |
| This example shows how to get a location by the location name.  |  | | --- | | $account = Get-VBRAzureAccount -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  Get-VBRAzureLocation -Subscription $subscription -Name "australiaeast" |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Specify the Name parameter value. Save it to the $account variable. 2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save it to the $subscription variable. 3. Run the Get-VBRAzureLocation cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. |

Related Commands

[Get-VBRAzureSubscription](get-vbrazuresubscription.md)


