---
title: "Get-VBRAzureNetworkSecurityGroup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazurenetworksecuritygroup.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Get-VBRAzureNetworkSecurityGroup

In this article

Short Description

Returns Microsoft Azure security groups.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all Microsoft Azure security groups.

|  |
| --- |
| Get-VBRAzureNetworkSecurityGroup -Subscription <VBRAzureSubscription> [-Location <VBRAzureLocation>]  [<CommonParameters>] |

* Get Microsoft Azure security groups by its ID.

|  |
| --- |
| Get-VBRAzureNetworkSecurityGroup -Subscription <VBRAzureSubscription> [-Id <string>] [-Location <VBRAzureLocation>]   [<CommonParameters>] |

* Get Microsoft Azure security groups by its name.

|  |
| --- |
| Get-VBRAzureNetworkSecurityGroup -Subscription <VBRAzureSubscription> [-Name <string[]>] [-Location <VBRAzureLocation>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Microsoft Azure security groups.

|  |
| --- |
| Important |
| This cmdlet does not support Microsoft Azure accounts with the Azure Service Manager type of a subscription (ASM, also known as a "classic" type subscription). |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Subscription | Specifies subscriptions associated with a Microsoft Azure account. | Accepts the [VBRAzureSubscription](vbrazuresubscription.md) object. To create this object, run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. | True | Named | True  (ByValue, ByPropertyName) |
| Location | Specifies a geographic location of the network security group. | Accepts the [VBRAzureLocation](vbrazurelocation.md) object. To get this object, run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. | False | Named | False |
| Id | Specifies Microsoft Azure security groups ID. The cmdlet will return security groups with the specified ID. | String | False | Named | False |
| Name | Specifies an array of Microsoft Azure security groups names. The cmdlet will return security groups with the specified names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureNetworkSecurityGroup](vbrazurenetworksecuritygroup.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Microsoft Azure Security Groups

|  |  |
| --- | --- |
| This example shows how to get all security groups that are available in Microsoft Azure.  |  | | --- | | $account = Get-VBRAzureAccount -Type ResourceManager -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account  Get-VBRAzureNetworkSecurityGroup -Subscription $subscription |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Specify the Type and Name parameter values. Save the result to the $account variable. 2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Save the result to the $subscription variable. 3. Run the Get-VBRAzureNetworkSecurityGroup cmdlet. Set the $subscription variable as the Subscription parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Microsoft Azure Security Groups by ID

|  |  |
| --- | --- |
| This example shows how to get the 374e0811-161e-4878-bc05-2ecba95fe4bd Microsoft Azure security group.  |  | | --- | | $account = Get-VBRAzureAccount -Type ResourceManager -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account  Get-VBRAzureNetworkSecurityGroup -Subscription $subscription -ID "374e0811-161e-4878-bc05-2ecba95fe4bd" |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Specify the Type and Name parameter values. Save the result to the $account variable. 2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Save the result to the $subscription variable. 3. Run the Get-VBRAzureNetworkSecurityGroup cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the ID parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Microsoft Azure Security Groups by Name

|  |  |
| --- | --- |
| This example shows how to get the Security Group 2000 Microsoft Azure security group.  |  | | --- | | $account = Get-VBRAzureAccount -Type ResourceManager -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account  Get-VBRAzureNetworkSecurityGroup -Subscription $subscription -Name "Security Group 2000" |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Specify the Type and Name parameter values. Save the result to the $account variable. 2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Save the result to the $subscription variable. 3. Run the Get-VBRAzureNetworkSecurityGroup cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. |

Related Commands

* [Get-VBRAzureAccount](get-vbrazureaccount.md)
* [Get-VBRAzureSubscription](get-vbrazuresubscription.md)

Page updated 3/1/2024

Page content applies to build 13.0.1.1071
