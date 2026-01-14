---
title: "Get-VBRAzureVMSize"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazurevmsize.html"
last_updated: "2/28/2024"
product_version: "13.0.1.1071"
---

# Get-VBRAzureVMSize

In this article

Short Description

Returns Microsoft Azure VM configuration options available for a subscription.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAzureVMSize -Subscription <VBRAzureSubscription> -Location <VBRAzureLocation> [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns VM configuration options available for a Microsoft Azure subscription.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Subscription | Specifies the subscription. The cmdlet will return VM configuration options associated with this subscription. | Accepts the [VBRAzureSubscription](vbrazuresubscription.md) object. To create this object, run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Location | Specifies the geographic location of the datacenter. | Accepts the [VBRAzureLocation](vbrazurelocation.md) object. To get this object, run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. | True | Named | True (ByProperty Name) |
| Name | Specifies the array of names. The cmdlet will return VM configuration options that match the specified names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureVMSize](vbrazurevmsize.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All VM Configuration Options Available for Subscription

|  |  |
| --- | --- |
| This example shows how to get all VM configuration options available for a subscription.  |  | | --- | | $account = Get-VBRAzureAccount -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  $location = Get-VBRAzureLocation -Subscription $subscription -Name "australiaeast"  Get-VBRAzureVMSize -Subscription $subscription -Location $location |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Specify the Name parameter value. Save it to the $account variable. 2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save it to the $subscription variable. 3. Run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Save it to the $location variable. 4. Run the Get-VBRAzureVMSize cmdlet. Set the $subscription variable as the Subscription parameter value. Set the $location variable as the Location parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting VM Configuration Options by Name

|  |  |
| --- | --- |
| This example shows how to get a VM configuration by the VM configuration name.  |  | | --- | | $account = Get-VBRAzureAccount -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  $location = Get-VBRAzureLocation -Subscription $subscription -Name "australiaeast"  Get-VBRAzureVMSize -Subscription $subscription -Location $location -Name "Standard\_G3" |  Perform the following steps:   1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Specify the Name parameter value. Save it to the $account variable. 2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save it to the $subscription variable. 3. Run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Save it to the $location variable. 4. Run the Get-VBRAzureVMSize cmdlet. Set the $subscription variable as the Subscription parameter value. Set the $location variable as the Location parameter value. Specify the Name parameter value. |

Related Commands

* [Get-VBRAzureSubscription](get-vbrazuresubscription.md)
* [Get-VBRAzureLocation](get-vbrazurelocation.md)

Page updated 2/28/2024

Page content applies to build 13.0.1.1071
