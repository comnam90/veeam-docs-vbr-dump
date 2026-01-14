---
title: "Get-VBRAzureVM"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazurevm.html"
last_updated: "5/3/2024"
product_version: "13.0.1.1071"
---

# Get-VBRAzureVM

In this article

Short Description

Returns Azure VMs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRAzureVM -Subscription <VBRAzureSubscription> -Location <VBRAzureLocation>  [<CommonParameters>] |

Detailed Description

This cmdlet returns Azure VMs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Subscription | Specifies subscriptions associated with a Microsoft Azure account. | Accepts the VBRAzureSubscription object. To create this object, run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. | True | Named | False |
| Location | Specifies Microsoft Azure region. | Accepts the VBRAzureLocation object. To get this object, run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureVM](vbrazurevm.md)

Examples

Getting Azure VMs

This example shows how to get Azure VMs.

|  |
| --- |
| $account = Get-VBRAzureAccount -Type ResourceManager -Name "AzureRM@tech.com"  $subscription = Get-VBRAzureSubscription -Account $account  $location = Get-VBRAzureLocation -Subscription $subscription  $VMs = Get-VBRAzureVM -Subscription $subscription -Location $location |

Perform the following steps:

1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Specify the Type and the Name parameter values. Save the result to the $account variable.
2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Save the result to the $subscription variable.
3. Run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Save the result to the $location variable.
4. Run the Get-VBRAzureVM cmdlet. Set the $subscription variable as the Subscription parameter value. Set the $location variable as the Location parameter value. Save the result to the $VMs variable.

Related Commands

* [Get-VBRAzureAccount](get-vbrazureaccount.md)
* [Get-VBRAzureSubscription](get-vbrazuresubscription.md)
* [Get-VBRAzureLocation](get-vbrazurelocation.md)

Page updated 5/3/2024

Page content applies to build 13.0.1.1071
