---
title: "New-VBRAzureApplianceTemplateDeploymentOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrazureappliancetemplatedeploymentoptions.html"
last_updated: "8/4/2025"
product_version: "13.0.1.1071"
---

# New-VBRAzureApplianceTemplateDeploymentOptions

In this article

Short Description

Defines deployment options for a helper appliance template.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Define options for a helper appliance template basing on options of a template existing in the same Microsoft Azure region.

|  |
| --- |
| New-VBRAzureApplianceTemplateDeploymentOptions -Template <VBRAzureApplianceTemplate> [-ResourceGroup <VBRAzureResourceGroup>] [-StorageAccount <VBRAzureStorageAccount>] [-VirtualNetwork <VBRAzureVirtualNetwork>] [-NetworkSubnet <VBRAzureNetworkSubnet>] [-Tags <VBRAzureTag[]>] [<CommonParameters>] |

* Define options for a helper appliance template by specifying a subscription and region.

|  |
| --- |
| New-VBRAzureApplianceTemplateDeploymentOptions -Subscription <VBRAzureSubscription> -Location <VBRAzureLocation> [-ResourceGroup <VBRAzureResourceGroup>] [-StorageAccount <VBRAzureStorageAccount>] [-VirtualNetwork <VBRAzureVirtualNetwork>] [-NetworkSubnet <VBRAzureNetworkSubnet>] [-Tags <VBRAzureTag[]>] [<CommonParameters>] |

Detailed Description

This cmdlet creates the object that defines options for a helper appliance template.

You can create a completely new template by specifying Subscription and Location parameters. Alternatively, you create a template basing on options of a template existing in the same Azure region by specifying the Template parameter. To specify other options for the new template, use the StorageAccount, VirtualNetwork and other parameters.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Template | Specifies a helper appliance template existing in the same Azure region. The cmdlet will modify settings of this helper appliance template and will deploy a new helper appliance template. | Accepts the VBRAzureApplianceTemplate object. To get this object, run the [Get-VBRAzureApplianceTemplate](get-vbrazureappliancetemplate.md) cmdlet. | True | Named | True |
| Subscription | Specifies the Microsoft Azure subscription where you want to deploy the template. | Accepts the VBRAzureSubscription object. To get this object, run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. | True | Named | True |
| Location | Specifies the Microsoft Azure region where you want to deploy the template. | Accepts the VBRAzureLocation object. To get this object, run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. | True | Named | True (ByPropertyName) |
| ResourceGroup | Specifies the resource group where you want to deploy the template.  If you do not specify this parameter, the cmdlet creates a resource group automatically. | Accepts the VBRAzureResourceGroup object. To get this object, run the [Get-VBRAzureResourceGroup](get-vbrazureresourcegroup.md) cmdlet. | False | Named | True (ByPropertyName) |
| StorageAccount | Specifies a storage account. The cmdlet will use this storage account to load services and components required for template creation.  If you do not specify this parameter, the cmdlet creates a storage account. This account will be deleted after the template is deployed. | Accepts the VBRAzureStorageAccount object. To get this object, run the [Get-VBRAzureStorageAccount](get-vbrazurestorageaccount.md) cmdlet. | False | Named | True (ByPropertyName) |
| VirtualNetwork | Specifies a virtual network. The cmdlet will use this virtual network for template creation.  If you do not specify this parameter, the cmdlet creates a virtual network. This network will be deleted after the template is deployed. | Accepts the VBRAzureVirtualNetwork object. To get this object, run the [Get-VBRAzureVirtualNetwork](get-vbrazurevirtualnetwork.md) cmdlet. | False | Named | True (ByPropertyName) |
| NetworkSubnet | Specifies a virtual network subnet. The cmdlet will use this virtual network subnet for template creation.  If you do not specify this parameter, the cmdlet creates a virtual network subnet. This subnet will be deleted after the template is deployed. | Accepts the VBRAzureNetworkSubnet object. To get this object, run the [Get-VBRAzureVirtualNetworkSubnet](get-vbrazurevirtualnetworksubnet.md) cmdlet. | False | Named | True (ByPropertyName) |
| Tags | Specifies tags that you want to assign to the template. | Accepts the VBRAzureTag[] object. To create this object, run the [New-VBRAzureTag](new-vbrazuretag.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAzureApplianceTemplateDeploymentOptions](vbrazureappliancetemplatedeploymentoptions.md)

Examples

This example shows how to define helper appliance template options.

|  |
| --- |
| $account = Get-VBRAzureAccount -Type ResourceManager -Name "RestoreToAzureRM@Veeam.com"  $subscription = Get-VBRAzureSubscription -Account $account -Name "VeeamDirectRestore2Azure"  $location = Get-VBRAzureLocation -Subscription $subscription -Name "swedencentral"  $templateOpt = New-VBRAzureApplianceTemplateDeploymentOptions -Subscription $subscription -Location $location |

Perform the following steps:

1. Run the [Get-VBRAzureAccount](get-vbrazureaccount.md) cmdlet. Set the ResourceManager value as the Type parameter value. Specify the Name parameter value. Save it to the $account variable.
2. Run the [Get-VBRAzureSubscription](get-vbrazuresubscription.md) cmdlet. Set the $account variable as the Account parameter value. Specify the Name parameter value. Save it to the $subscription variable.
3. Run the [Get-VBRAzureLocation](get-vbrazurelocation.md) cmdlet. Set the $subscription variable as the Subscription parameter value. Specify the Name parameter value. Save it to the $location variable.
4. Run the New-VBRAzureApplianceTemplateDeploymentOptions cmdlet. Set the $subscription variable as the Subscription parameter value. Set the $location variable as the Location parameter value. Save it to the $templateOpt variable.

Related Commands

* [Get-VBRAzureAccount](get-vbrazureaccount.md)
* [Get-VBRAzureSubscription](get-vbrazuresubscription.md)
* [Get-VBRAzureLocation](get-vbrazurelocation.md)

Page updated 8/4/2025

Page content applies to build 13.0.1.1071
