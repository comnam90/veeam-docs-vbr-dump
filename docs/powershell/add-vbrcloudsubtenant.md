---
title: "Add-VBRCloudSubTenant"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrcloudsubtenant.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Add-VBRCloudSubTenant


Short Description

Creates cloud subtenant accounts.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRCloudSubTenant -Tenant <VBRCloudTenant> -Name <string> -Password <string> -Resources <VBRCloudSubTenantResource[]> [-Description <string>] [-HashedPassword] [-Disabled]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new cloud subtenant account.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Tenant | Specifies the parent tenant. The cmdlet will use resources of this tenant as parent resources for the subtenant. | Accepts the [VBRCloudTenant](vbrcloudtenant.md) object. To get this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | True | Named | True (ByValue, |
| Name | Specifies the name you want to assign to the subtenant account.  The subtenant name must meet the following requirements:   * The maximum length of the subtenant name is 128 characters. It is recommended that you create short subtenant names to avoid problems with long paths to backup files on the cloud repository. * The subtenant name may contain space characters. * The subtenant name must not contain the following characters: \/:\*?\"<>|=; as well as Unicode characters. * The subtenant name must not end with the period character [.]. | String | True | Named | False |
| Password | Specifies the password you want to set to the subtenant account. | String | True | Named | False |
| Recources | Specifies the quota of the subtenant backup resources you want to give to the subtenant. | Accepts the [VBRCloudSubTenantResource[]](vbrcloudsubtenantresource.md) object. To get this object, run the [New-VBRCloudSubtenantResource](new-vbrcloudsubtenantresource.md) cmdlet. | True | Named | False |
| Description | Specifies the description of the cloud subtenant account. | String | False | Named | False |
| HashedPassword | Defines that you submit the hashed password. The hashed passwords are stored in Veeam backup database.  Use this parameter, for example, to restore subtenant accounts. | SwitchParameter | False | Named | False |
| Disabled | Defines that the cloud subtenant is disabled. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudSubTenant](vbrcloudsubtenant.md)

Examples

Creating Cloud Subtenant Account

This example shows how to create a cloud subtenant account.

|  |
| --- |
| $parent = Get-VBRCloudTenant -Name "ABC Company"  $parentresource = $parent.Resources[0]  $subtenantquota = New-VBRCloudSubtenantResource -Parent $parentresource -RepositoryFriendlyName "ABC Cloud Repository" -Unlimited  $tenant = Get-VBRCloudTenant -Name "Alpha"  Add-VBRCloudSubTenant -Tenant $tenant -Name "Alpha" -Password "Pass123" -Resources $subtenantquota |

Perform the following steps:

1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $parent variable.
2. Get the parent resources using the Resources property of the [VBRCloudTenantResource](vbrcloudtenantresource.md) object saved to the $parent variable. Save the result to the $parentresource variable.
3. Run the [New-VBRCloudSubTenantResource](new-vbrcloudsubtenantresource.md) cmdlet for details. Set the $parentresource variable as the Parent parameter value. Specify the RepositoryFriendlyName parameter value. Provide the Unlimited parameter. Save the result to the $subtenantquota variable.
4. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable.
5. Run the Add-VBRCloudSubTenant cmdlet. Specify the following settings:

* Set the $tenant variable as the Tenant parameter value.
* Specify the Name and the Password parameter values.
* Set the $subtenantquota variable as the Resources parameter value.

Related Commands

[Get-VBRCloudTenant](get-vbrcloudtenant.md)


