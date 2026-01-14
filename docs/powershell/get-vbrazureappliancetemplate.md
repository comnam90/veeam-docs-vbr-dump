---
title: "Get-VBRAzureApplianceTemplate"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrazureappliancetemplate.html"
last_updated: "7/30/2025"
product_version: "13.0.1.1071"
---

# Get-VBRAzureApplianceTemplate

In this article

Short Description

Returns deployed helper appliance templates.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all helper appliance templates.

|  |
| --- |
| Get-VBRAzureApplianceTemplate [<CommonParameters>] |

* Get a helper appliance template by ID.

|  |
| --- |
| Get-VBRAzureApplianceTemplate [-Id <guid[]>] [<CommonParameters>] |

* Get helper appliance templates in a specific subscription or region.

|  |
| --- |
| Get-VBRAzureApplianceTemplate [-Subscription <VBRAzureSubscription[]>] [-Location <VBRAzureLocation[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns deployed helper appliance templates.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of IDs. The cmdlet will return helper appliance templates with the specified IDs. | Guid[] | False | Named | True |
| Subscription | Specifies the Microsoft Azure subscription from which you want to return the deployed helper appliance templates. | Accepts the VBRAzureSubscription object. To get this object, run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. | False | Named | True |
| Location | Specifies the Microsoft Azure region from which you want to return the deployed helper appliance templates. | Accepts the VBRAzureLocation object. To get this object, run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureApplianceTemplate](vbrazureappliancetemplate.md)

Examples

This example shows how to get all helper appliance templates deployed in a subscription.

|  |
| --- |
| $account = Get-VBRAzureAccount -Type ResourceManager -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  $template = Get-VBRAzureApplianceTemplate -Subscription $subscription |

Perform the following steps:

1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Set the ResourceManager value as the Type parameter value. Specify the Name parameter value. Save it to the $account variable.
2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save it to the $subscription variable.
3. Run the Get-VBRAzureApplianceTemplate cmdlet. Set the $subscription variable as the Subscription parameter value. Set the $location variable as the Location parameter value. Save it to the $template variable.

Related Commands

* [Get-VBRAzureAccount](get-vbrazureaccount.md)
* [Get-VBRAzureSubscription](get-vbrazuresubscription.md)

Page updated 7/30/2025

Page content applies to build 13.0.1.1071
