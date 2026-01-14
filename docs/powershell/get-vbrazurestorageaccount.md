---
title: "Get-VBRAzureStorageAccount"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazurestorageaccount.html"
last_updated: "12/13/2023"
product_version: "13.0.1.1071"
---

# Get-VBRAzureStorageAccount

In this article

Short Description

Returns Microsoft Azure storage accounts available for a subscription.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAzureStorageAccount -Subscription <VBRAzureSubscription> [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns storage accounts available for a Microsoft Azure subscription.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Subscription | Specifies the subscription. The cmdlet will return storage accounts associated with this subscription. | Accepts the [VBRAzureSubscription](vbrazuresubscription.md) object. To create this object, run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the array of names. The cmdlet will return storage accounts that match the specified names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureStorageAccount](vbrazurestorageaccount.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Storage Accounts Available for Subscription

|  |  |
| --- | --- |
| This example shows how to get all storage accounts associated with a subscription.  |  | | --- | | $account = Get-VBRAzureAccount -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  Get-VBRAzureStorageAccount -Subscription $subscription |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Specify the Name parameter value. Save it to the $account variable. 2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save it to the $subscription variable. 3. Run the Get-VBRAzureStorageAccount cmdlet. Set the $subscription variable as the Subscription parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Storage Account by Name

|  |  |
| --- | --- |
| This example shows how to get a storage account by the storage account name.  |  | | --- | | $account = Get-VBRAzureAccount -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  Get-VBRAzureStorageAccount -Subscription $subscription -Name "VeeamDirectRestore2AzureStorage" |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Specify the Name parameter value. Save it to the $account variable. 2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save it to the $subscription variable. 3. Run the Get-VBRAzureStorageAccount cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. |

Related Commands

[Get-VBRAzureSubscription](get-vbrazuresubscription.md)

Page updated 12/13/2023

Page content applies to build 13.0.1.1071
