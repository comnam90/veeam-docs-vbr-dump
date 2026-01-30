---
title: "Set-VBRAzureContainer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrazurecontainer.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# Set-VBRAzureContainer


Short Description

Modifies a scope of Azure VMs, Azure tags or Azure Availability Zone for a protection group.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRAzureContainer -Container <VBRAzureContainer> [-Subscription <VBRAzureSubscription>] [-Location <VBRAzureLocation>] [-Entity <Object[]>] [-ExcludeEntities] [-ExcludedEntity <Object[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies a scope of Azure VMs, Azure tags or Azure Availability Zone for a protection group.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Container | Specifies a scope of the following entities that you want to modify:   * Azure VMs. * Azure tags. * Azure Availability Zone. | Accepts the VBRAzureContainer object. To create this object, run the [New-VBRAzureContainer](new-vbrazurecontainer.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Subscription | Specifies subscriptions associated with a Microsoft Azure account. | Accepts the VBRAzureSubscription object. To create this object, run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| Location | Specifies Microsoft Azure region. | Accepts the VBRAzureLocation object. To get this object, run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| Entity | Specifies an array of the following entities that the cmdlet till add to a scope of a protection group:   * Azure VMs. * Azure tags. * Azure Availability Zone. | Accepts the Object[] object. To get this object, run the following  cmdlets:   * [Get-VBRAzureVM](get-vbrazurevm.md) * [New-VBRAzureTag](new-vbrazuretag.md) * [Get-VBRAzureLocation](get-vbrazurelocation.md) | False | Named | True (ByValue, ByPropertyName) |
| ExcludeEntities | Specifies an array of the following entities that the cmdlet will exclude from a scope of a protection group:   * Azure VMs. * Azure tags. * Azure Availability Zone. | SwitchParameter | False | Named | True (ByValue, ByPropertyName) |
| ExcludedEntity | Specifies an array of the following entities that the cmdlet will exclude from a scope of a protection group:   * Azure VMs. * Azure tags. * Azure Availability Zone. | Accepts the Object[] object. To get this object, run the following  cmdlets:   * [Get-VBRAzureVM](get-vbrazurevm.md) * [New-VBRAzureTag](new-vbrazuretag.md) * [Get-VBRAzureLocation](get-vbrazurelocation.md) | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureContainer](vbrazurecontainer.md)

Examples

Modifying Scope of Azure Entities for Protection Group

This example shows how to modify the scope of Azure entities. The cmdlet will include Azure VMs into scope instead of Azure Availability Zone.

|  |
| --- |
| $account = Get-VBRAzureAccount -Type ResourceManager -Name "AzureRM@tech.com"  $subscription = Get-VBRAzureSubscription -Account $account  $location = Get-VBRAzureLocation -Subscription $subscription  $scope = New-VBRAzureContainer -Subscription $subscription -Location $location -Entity $location  $VMs = Get-VBRAzureVM -Subscription $subscription -Location $location  $VMScope = Set-VBRAzureContainer -Container $scope -Entity $VMs |

Perform the following steps:

1. Define the Azure Availability Zone protection scope:

1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Specify the Type and the Name parameter values. Save the result to the $account variable.
2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Save the result to the $subscription variable.
3. Run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Save the result to the $location variable.
4. Run the [New-VBRAzureContainer](new-vbrazurecontainer.md) cmdlet. Specify the Subscription, Location and Entity parameter values. Save the result to the $scope variable.

1. Run the [Get-VBRAzureVM](get-vbrazurevm.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Set the $location variable as the Location parameter value. Save the result to the $VMs variable.
2. Run the Set-VBRAzureContainer cmdlet. Set the $scope variable as the Container parameter value. Set the $VMs variable as the Entity parameter value. Save the result to the $VMScope variable.

Related Commands

* [Get-VBRAzureAccount](get-vbrazureaccount.md)
* [Get-VBRAzureSubscription](get-vbrazuresubscription.md)
* [Get-VBRAzureLocation](get-vbrazurelocation.md)
* [New-VBRAzureContainer](new-vbrazurecontainer.md)
* [Get-VBRAzureVM](get-vbrazurevm.md)


