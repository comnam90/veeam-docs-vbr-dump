---
title: "New-VBRCloudSubTenantResource"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrcloudsubtenantresource.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# New-VBRCloudSubTenantResource

In this article

Short Description

Creates quotas of cloud subtenant resources.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Create a quota with limited disk space.

|  |
| --- |
| New-VBRCloudSubTenantResource -Parent <VBRCloudTenantResource> -RepositoryFriendlyName <string> -Quota <int64>  [<CommonParameters>] |

* Create a quota with unlimited disk space.

|  |
| --- |
| New-VBRCloudSubTenantResource -Parent <VBRCloudTenantResource> -RepositoryFriendlyName <string> [-Unlimited]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new [VBRCloudSubTenantResource](vbrcloudsubtenantresource.md) object. This object contains a quota of the tenant backup resources.

The subtenant quota is a part of subtenant account. To assign the quota to a subtenant, run the [Add-VBRCloudSubTenant](add-vbrcloudsubtenant.md) cmdlet and use the created [VBRCloudSubTenantResource](vbrcloudsubtenantresource.md) object.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Parent | Specifies the backup resources of the cloud tenant. The disk space available under the tenant account will be used as parent resources for creating the subtenant quota.  Use the Quota or the Unlimited parameter to indicate the amount of disk space you want to give to a subtenant. | Accepts the [VBRCloudTenantResource](vbrcloudtenantresource.md) object. To get this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | True | Named | True (ByValue, |
| RepositoryFriendlyName | Specifies the name you want to give to the subtenant quota.  This name will be displayed in the list of backup repositories at the subtenant’s side. | String | True | Named | True (ByProperty Name) |
| Quota | Specifies the amount of space you want to give to the subtenant on the selected backup repository.  Permitted value: 1 to 2097151  (GB). | Int64 | True | Named | True (ByProperty Name) |
| Unlimited | Defines that the quota of resources has unlimited disk space.  With unlimited quota, the subtenant will be able to use all disk space allocated to the parent. | SwitchParameter | True | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudSubtenantResource](vbrcloudsubtenantresource.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Quota of Resources for Subtenant with Limited Disk Space

|  |  |
| --- | --- |
| This example shows how to create a quota of resources for a subtenant with a limited disk space.  |  | | --- | | $parent = Get-VBRCloudTenant -Name "ABC Company"  $parentresources = $parent.Resources[0]  $subtenantquota = New-VBRCloudSubtenantResource -Parent $parentresources -RepositoryFriendlyName "ABC Cloud Repository" -Quota 10 |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $parent variable. 2. Get the parent resources using the Resources property of the [VBRCloudTenantResource](vbrcloudtenantresource.md) object saved to the $parent variable. Save the result to the $parentresources variable. 3. Run the New-VBRCloudSubtenantResource cmdlet. Specify the following settings:  * Set the $parentresources variable as the Parent parameter value. * Specify the RepositoryFriendlyName parameter value. * Specify the Quota parameter value. * Save the result to the $subtenantquota variable for future use. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Quota of Resources for Subtenant with Unlimited Disk Space

|  |  |
| --- | --- |
| This example shows how to create a quota of resources for a subtenant with unlimited disk space.  |  | | --- | | $parent = Get-VBRCloudTenant -Name "ABC Company"  $parentresource = $parent.Resources[0]  $subtenantquota = New-VBRCloudSubtenantResource -Parent $parentresource -RepositoryFriendlyName "ABC Cloud Repository" -Unlimited |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $parent variable. 2. Get the parent resources using the Resources property of the [VBRCloudTenantResource](vbrcloudtenantresource.md) object saved to the $parent variable. Save the result to the $parentresources variable. 3. Run the New-VBRCloudSubtenantResource cmdlet. Specify the following settings:  * Set the $parentresources variable as the Parent parameter value.  * Specify the RepositoryFriendlyName parameter value. * Provide the Unlimited parameter.  * Save the result to the $subtenantquota variable for future use. |

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [New-VBRCloudTenantResource](new-vbrcloudtenantresource.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
