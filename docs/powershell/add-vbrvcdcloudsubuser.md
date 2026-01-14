---
title: "Add-VBRvCDCloudSubUser"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrvcdcloudsubuser.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Add-VBRvCDCloudSubUser

In this article

Short Description

Creates Cloud Director subuser accounts.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRvCDCloudSubUser -CloudProvider <VBRCloudProvider> -vCDCloudOrganizationUser <VBRvCDCloudOrganizationUser> -Resources <VBRCloudSubUserResource[]> [-Description <string>] [-Disabled]  [<CommonParameters>] |

Detailed Description

This cmdlet creates Cloud Director subuser accounts from the tenant side. You can use these accounts to back up Windows and Linux computers that are protected by Veeam Agent. The backups of these machines will be stored on the cloud repository.

|  |
| --- |
| ![Add-VBRvCDCloudSubUser ](images/icon_note.webp) Note: |
| Consider the following:   * This cmdlet is available for tenants only. * Run the [Add-VBRvCDCloudSubTenant](add-vbrvcdcloudsubtenant.md) cmdlet to create the Cloud Director subtenant on the provider side. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudProvider | Specifies a cloud service provider. The resources of this cloud service provider will be a parent for the subuser. | Accepts the [VBRCloudProvider](vbrcloudprovider.md) object. To get this object, run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. | True | Named | True (ByValue, |
| VBRvCDCloudOrganizationUser | Specifies Cloud Director user accounts that you want to add. | Accepts the VBRvCDCloudOrganizationUser object. To get this object, run the [Get-VBRvCDCloudOrganizationUser](get-vbrvcdcloudorganizationuser.md) cmdlet. | True | Named | True (ByValue, |
| Resources | Specifies the quota of the subtenant backup resources that you want to give to the subtenant. | Accepts the [VBRCloudSubUserResource[]](vbrcloudsubuserresource.md) object. To create this object, run the [New-VBRCloudSubUserResource](new-vbrcloudsubuserresource.md) cmdlet. | True | Named | False |
| Description | Specifies a description of a Cloud Director subuser account. | String | False | Named | False |
| Disabled | Defines that a Cloud Director subuser is disabled. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRvCDCloudSubUser

Examples

Creating Cloud Director Subuser Account on Tenant Side

This example shows how to create a Cloud Director subuser account on the tenant side.

|  |
| --- |
| $provider = Get-VBRCloudProvider -Name "vCDProvider"  $user = Get-VBRvCDCloudOrganizationUser -Name "vCDCloudUser"  $rep = Get-VBRBackupRepository -Name "vCD Repository"  $resources = New-VBRCloudSubUserResource -CloudRepository $rep -RepositoryFriendlyName "Vancouver Repository" -Quota 50  Add-VBRvCDCloudSubUser -CloudProvider $provider -vCDCloudOrganizationUser $user -Resources $resources |

Perform the following steps:

1. Run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. Specify the Name parameter value. Save the result to the $provider variable.
2. Run the [Get-VBRvCDCloudOrganizationUser](get-vbrvcdcloudorganizationuser.md) cmdlet. Specify the Name parameter value. Save the result to the $user variable.
3. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $rep variable.
4. Run the [New-VBRCloudSubUserResource](new-vbrcloudsubuserresource.md) cmdlet. Set the $rep variable as the CloudRepository parameter value. Specify the RepositoryFriendlyName and the Quota parameter values. Save the result to the $resources variable.
5. Run the Add-VBRvCDCloudSubUser cmdlet. Set the $provider variable as the CloudProvider parameter value. Set the $user variable as the vCDCloudOrganizationUser parameter value. Set the $resources variable as the Resources parameter value.

Related Commands

* [Get-VBRCloudProvider](get-vbrcloudprovider.md)
* [Get-VBRvCDCloudOrganizationUser](get-vbrvcdcloudorganizationuser.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [New-VBRCloudSubUserResource](new-vbrcloudsubuserresource.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
