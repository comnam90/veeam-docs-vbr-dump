---
title: "Get-VBRAzureResourceGroup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazureresourcegroup.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Get-VBRAzureResourceGroup

In this article

Short Description

Returns Microsoft Azure resource groups available for a subscription.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAzureResourceGroup -Subscription <VBRAzureSubscription> [-Name <string[]>] [-Location <VBRAzureLocation>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns resource groups available for a selected subscription.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Subscription | Specifies the subscription. The cmdlet will return resource groups associated with this subscription. | Accepts the [VBRAzureSubscription](vbrazuresubscription.md) object. To create this object, run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. | True | Named | True (ByValue, |
| Name | Specifies the array of names. The cmdlet will return resource groups that match the specified names. | String[] | False | Named | False |
| Location | Specifies geographic locations of Microsoft Azure datacenters available for a resource group. | Accepts the [VBRAzureLocation](vbrazurelocation.md) object. To get this object, run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureResourceGroup](vbrazureresourcegroup.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Resource Groups Available for Subscription

|  |  |
| --- | --- |
| This example shows how to get all resource groups associated with a subscription.  |  | | --- | | $account = Get-VBRAzureAccount -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  Get-VBRAzureResourceGroup -Subscription $subscription |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Specify the Name parameter value. Save it to the $account variable. 2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save it to the $subscription variable. 3. Run the Get-VBRAzureResourceGroup cmdlet. Set the $subscription variable as the Subscription parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Resource Group by Name

|  |  |
| --- | --- |
| This example shows how to get a resource group by the resource group name.  |  | | --- | | $account = Get-VBRAzureAccount -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  Get-VBRAzureResourceGroup -Subscription $subscription -Name "VeeamResourceGroup" |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Specify the Name parameter value. Save it to the $account variable. 2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save it to the $subscription variable. 3. Run the Get-VBRAzureResourceGroup cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. |

Related Commands

[Get-VBRAzureSubscription](get-vbrazuresubscription.md)

Page updated 2/28/2024

Page content applies to build 13.0.1.1071
