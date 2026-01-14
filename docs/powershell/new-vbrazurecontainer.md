---
title: "New-VBRAzureContainer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrazurecontainer.html"
last_updated: "5/3/2024"
product_version: "13.0.1.1071"
---

# New-VBRAzureContainer

In this article

Short Description

Defines a scope of Azure VMs, Azure tags or Azure Availability Zone for a protection group.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRAzureContainer -Subscription <VBRAzureSubscription> -Location <VBRAzureLocation> -Entity <Object[]> [-ExcludeEntities] [-ExcludedEntity <Object[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet defines the [VBRAzureContainer](vbrazurecontainer.md) object. This object contains a scope of Azure VMs, Azure tags or Azure Availability Zone for a protection group.

Use this object to create a protection group with the [Add-VBRProtectionGroup](add-vbrprotectiongroup.md) cmdlet. After you create a protection group, Veeam Backup & Replication will deploy Veeam Agent on Azure VMs, Azure tags or Azure Availability Zone added to the scope of the protection group.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Subscription | Specifies subscriptions associated with a Microsoft Azure account. | Accepts the VBRAzureSubscription object. To create this object, run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Location | Specifies Microsoft Azure region. | Accepts the VBRAzureLocation object. To get this object, run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Entity | Specifies an array of the following entities that the cmdlet till add to a scope of a protection group:   * Azure VMs. * Azure tags. * Azure Availability Zone. | Accepts the Object[] object. To get this object, run the following  cmdlets:   * [Get-VBRAzureVM](get-vbrazurevm.md) * [New-VBRAzureTag](new-vbrazuretag.md) * [Get-VBRAzureLocation](get-vbrazurelocation.md) | True | Named | True (ByValue, ByPropertyName) |
| ExcludeEntities | Specifies an array of the following entities that the cmdlet will exclude from a scope of a protection group:   * Azure VMs. * Azure tags. * Azure Availability Zone. | SwitchParameter | False | Named | True (ByValue, ByPropertyName) |
| ExcludedEntity | Specifies an array of the following entities that the cmdlet will exclude from a scope of a protection group:   * Azure VMs. * Azure tags. * Azure Availability Zone. | Accepts the Object[] object. To get this object, run the following  cmdlets:   * [Get-VBRAzureVM](get-vbrazurevm.md) * [New-VBRAzureTag](new-vbrazuretag.md) * [Get-VBRAzureLocation](get-vbrazurelocation.md) | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureContainer](vbrazurecontainer.md)

Examples

Defining Scope of Azure VMs for Protection Group

This example shows how to define the scope of Azure VMs to add them to a protection group.

|  |
| --- |
| $account = Get-VBRAzureAccount -Type ResourceManager -Name "AzureRM@tech.com"  $subscription = Get-VBRAzureSubscription -Account $account  $location = Get-VBRAzureLocation -Subscription $subscription  $VMs = Get-VBRAzureVM -Subscription $subscription -Location $location  $scope = New-VBRAzureContainer -Subscription $subscription -Location $location -Entity $VMs |

Perform the following steps:

1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Specify the Type and the Name parameter values. Save the result to the $account variable.
2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Save the result to the $subscription variable.
3. Run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Save the result to the $location variable.
4. Run the [Get-VBRAzureVM](get-vbrazurevm.md) cmdlet.  Set the $subscription variable as the Subscription parameter value. Set the $location variable as the Location parameter value. Save the result to the $VMs variable.
5. Run the New-VBRAzureContainer cmdlet. Set the $subscription variable as the Subscription parameter value. Set the $location variable as the Location parameter value. Set the $VMs variable as the Entity parameter value. Save the result to the $scope variable.

Related Commands

* [Get-VBRAzureAccount](get-vbrazureaccount.md)
* [Get-VBRAzureSubscription](get-vbrazuresubscription.md)
* [Get-VBRAzureLocation](get-vbrazurelocation.md)
* [Get-VBRAzureVM](get-vbrazurevm.md)

Page updated 5/3/2024

Page content applies to build 13.0.1.1071
