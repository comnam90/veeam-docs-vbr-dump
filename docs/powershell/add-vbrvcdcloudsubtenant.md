---
title: "Add-VBRvCDCloudSubTenant"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrvcdcloudsubtenant.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Add-VBRvCDCloudSubTenant

In this article

Short Description

Creates Cloud Director subtenant accounts.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRvCDCloudSubTenant -vCDTenant <VBRvCDCloudTenant> -vCDOrganizationUser <VBRvCloudOrganizationUser> -Resources <VBRCloudSubTenantResource[]> [-Description <String>] [-Disabled]  [<CommonParameters>] |

Detailed Description

This cmdlet creates new Cloud Director subtenant accounts.

|  |
| --- |
| ![Add-VBRvCDCloudSubTenant](images/icon_note.webp) Note: |
| Before creating a Cloud Director subtenant account, you must perform the following:   * Add the Cloud Director tenant into your Veeam Backup & Replication infrastructure. * Create users in VMware Cloud Director. The Cloud Director users must be granted the role, different from the administrator one. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| vCDTenant | Specifies the Cloud Director tenant account. Veeam Backup & Replication will check for the existing users on this tenant, to add them as the subtenant into the backup infrastructure. | Accepts the [VBRvCDCloudTenant](vbrvcdcloudtenant.md) object. To get this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | True | Named | True, (ByValue, ByPropertyName) |
| vCDOrganizationUser | Specifies the Cloud Director user account that you want to add to the subtenant. | Accepts the VBRvCloudOrganizationUser object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | True | Named | True, (ByValue, ByPropertyName) |
| Resources | Specifies the quota of backup resources that you want to allocate to the Cloud Director subtenant accounts. | Accepts the [VBRCloudTenantResource](vbrcloudtenantresource.md) object. To get this object, run the [New-VBRCloudSubTenantResource](new-vbrcloudsubtenantresource.md) cmdlet. | True | Named | False |
| Description | Specifies the description of the Cloud Director subtenant accounts. | String | False | Named | False |
| Disabled | Defines that the subtenant is disabled. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRvCDCloudSubTenant

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Cloud Director Subtenant Account

|  |  |
| --- | --- |
| This example shows how to add a Cloud Director subtenant account to your Veeam Backup & Replication infrastructure. The subtenant quota is set to 50 GB.  |  | | --- | | $vcduser = Find-VBRvCloudEntity -OrganizationUser -Name vCDUser  $vcdtenant = Get-VBRCloudTenant -Name "vCDTenant"  $parent = $vcdtenant.Resources[0]  $subRes = New-VBRCloudSubTenantResource -Parent $parent -RepositoryFriendlyName "Cloudrepository" -Quota 50  Add-VBRvCDCloudSubTenant -vCDOrganizationUser $vcduser -vCDTenant $vcdtenant -Resources $subRes -Description "NewCloudSubTenant" |  Perform the following steps:   1. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Provide the OrganizationUser parameter. Specify the Name parameter value. Save the result to the $vcduser variable. 2. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $vcdtenant variable. 3. Get the parent resources. Use the Resources property of the VBRCloudTenantResource object saved to the $vcdtenant variable. Save the result to the $parent variable. 4. Run the [New-VBRCloudSubTenantResource](new-vbrcloudsubtenantresource.md) cmdlet. Set the $parent variable as the Parent parameter value. Specify the RepositoryFriendlyName and the Quota parameter values. Save the result to the $subRes variable. 5. Run the Add-VBRvCDCloudSubTenant cmdlet. Specify the following settings:  * Set the $vcduser variable as the vCDOrganizationUser parameter value. * Set the $vcdtenant variable as the vCDTenant parameter value. * Set the $subRes variable as the Resources parameter value. * Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Cloud Director Subtenant Account with Unlimited Quota

|  |  |
| --- | --- |
| This example shows how to add a Cloud Director subtenant account to your Veeam Backup & Replication infrastructure. The subtenant quota is unlimited.  |  | | --- | | $vcduser = Find-VBRvCloudEntity -OrganizationUser -Name vCDUser  $vcdtenant = Get-VBRCloudTenant -Name "vCDTenant"  $subRes = New-VBRCloudSubTenantResource -Parent $vcdtenant.Resources[0] -RepositoryFriendlyName "Cloudrepository" -Unlimited  Add-VBRvCDCloudSubTenant -vCDOrganizationUser $vcduser -vCDTenant $vcdtenant  -Resources $subRes -Description "NewCloudSubTenant" |  Perform the following steps:   1. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Provide the OrganizationUser parameter. Specify the Name parameter value. Save the result to the $vcduser variable. 2. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $vcdtenant variable. 3. Run the [New-VBRCloudSubTenantResource](new-vbrcloudsubtenantresource.md) cmdlet. Set the Resources property of the VBRCloudTenantResource object saved to the $vcdtenant variable as the Parent parameter value. Specify the RepositoryFriendlyName parameter value. Provide the Unlimited parameter. Save the result to the $subRes variable. 4. Run the Add-VBRvCDCloudSubTenant cmdlet. Specify the following settings:  * Set the $vcduser variable as the vCDOrganizationUser parameter value. * Set the $vcdtenant variable as the vCDTenant parameter value. * Set the $subRes variable as the Resources parameter value.  * Specify the Description parameter value. |

Related Commands

* [Find-VBRvCloudEntity](find-vbrvcloudentity.md)
* [Get-VBRCloudTenant](get-vbrcloudtenant.md)
* [New-VBRCloudSubTenantResource](new-vbrcloudsubtenantresource.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
