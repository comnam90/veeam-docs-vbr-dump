---
title: "Get-VBRAzureSubscription"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazuresubscription.html"
last_updated: "12/13/2023"
product_version: "13.0.1.1071"
---

# Get-VBRAzureSubscription


Short Description

Returns subscriptions associated with a Microsoft Azure account.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get subscriptions by the subscriptions name.

|  |
| --- |
| Get-VBRAzureSubscription -Account <VBRAzureAccount> [-Name <string[]>]  [<CommonParameters>] |

* Get subscriptions by the subscriptions ID.

|  |
| --- |
| Get-VBRAzureSubscription -Account <VBRAzureAccount> [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns subscriptions associated with a selected Microsoft Azure account.

|  |
| --- |
| Important |
| This cmdlet does not support Microsoft Azure accounts with the Azure Service Manager type of a subscription (ASM, also known as a "classic" type subscription). |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Account | Specifies the account. The cmdlet will return subscriptions associated with this account. | Accepts the [VBRAzureAccount](vbrazureaccount.md) object. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet to get this object. | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the array of names of the subscriptions you want to get. | String[] | False | Named | False |
| Id | Specifies the array of IDs of the subscriptions you want to get. | Guid[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureSubscription](vbrazuresubscription.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Subscriptions for Microsoft Azure Account

|  |  |
| --- | --- |
| This example shows how to get all subscriptions associated with an account.  |  | | --- | | $account = Get-VBRAzureAccount -Type ResourceManager -Name "RestoreToAzureRM@Veeam.com"  Get-VBRAzureSubscription -Account $account |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Set the ResourceManager value as the Type parameter value. Specify the Name parameter value. Save it to the $account variable. 2. Run the Get-VBRAzureSubscription cmdlet. Set the $account variable as the Account parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Subscription by Name

|  |  |
| --- | --- |
| This example shows how to get a subscription by the subscription name.  |  | | --- | | $account = Get-VBRAzureAccount -Type ResourceManager -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure" |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Set the ResourceManager value as the Type parameter value. Specify the Name parameter value. Save it to the $account variable. 2. Run the Get-VBRAzureSubscription cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save it to the $subscription variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Subscription by ID

|  |  |
| --- | --- |
| This example shows how to get a subscription by the subscription ID.  |  | | --- | | $account = Get-VBRAzureAccount -Type ResourceManager -Name "RestoreToAzureRM@Veeam.com"  Get-VBRAzureSubscription -Account $account | Where-Object Id -eq "f482cd54-454d-419f-9ec2-f388796091f9" |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Set the ResourceManager value as the Type parameter value. Specify the Name parameter value. Save it to the $account variable. 2. Run the Get-VBRAzureSubscription cmdlet. Set the $account variable as the Account parameter value. Pass the result to the Where-Object cmdlet to select the subscriptions with the Id property that equals f482cd54-454d-419f-9ec2-f388796091f9. |

Related Commands

[Get-VBRAzureAccount](get-vbrazureaccount.md)


