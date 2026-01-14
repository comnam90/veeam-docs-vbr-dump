---
title: "New-VBRCloudTenantResource"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrcloudtenantresource.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# New-VBRCloudTenantResource

In this article

Short Description

Creates the [VBRCloudTenantResource](vbrcloudtenantresource.md) objects that contain backup resources.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

|  |
| --- |
| New-VBRCloudTenantResource -Repository <CBackupRepository> -RepositoryFriendlyName <String> -Quota <Int64> [-EnableWanAccelerator] [-WanAccelerator <CWanAccelerator>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new [VBRCloudTenantResource](vbrcloudtenantresource.md) object. This object contains the backup resources settings and is used further to apply these settings to a cloud tenant account.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Repository | Specifies the backup repository in your backup infrastructure you want to expose to the tenant.  You can specify simple or scale-out backup repositories.  You cannot specify cloud repositories or individual scale-out repositories extents. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | False |
| RepositoryFriendlyName | Specifies a name for the cloud repository you want to present to the tenant. The name you enter will be displayed in the list of backup repositories at the tenant’s side. | String | True | Named | False |
| Quota | Specifies the amount of space you want to allocate to the tenant on the selected backup repository.  Permitted value: 1 to 2097151  (GB). | Int64 | True | Named | False |
| EnableWanAccelerator | Enables the option to use WAN accelerators for backup jobs to cloud repositories.  Use the WanAccelerator parameter to set the WAN accelerator. | SwitchParameter | False | Named | False |
| WanAccelerator | Specifies the WAN accelerator for the EnableWanAccelerator parameter. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudTenantResource](vbrcloudtenantresource.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Object with Tenant Quota

|  |  |
| --- | --- |
| This example shows how to create an object containing backup resources with the following settings:   * The cloud repository is named Standard Tier Repository. * The tenant quota is set to 10 GB.   |  | | --- | | $repo1 = Get-VBRBackupRepository -Name "Backups Vol2"  $standard1 = New-VBRCloudTenantResource -Repository $repo1 -RepositoryFriendlyName "Standard Tier Repository" -Quota 10 |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repo1 variable. 2. Run the New-VBRCloudTenantResource cmdlet. Specify the following settings:  * Set the $repo1 variable as the Repository parameter value. * Specify the RepositoryFriendlyName parameter value. * Specify the Quota parameter value. * Save the result to the $standard1 variable to be used with other cmdlets. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Object with Tenant Quota and WAN Acceleration

|  |  |
| --- | --- |
| This example shows how to create an object containing backup resources with the following settings:   * The cloud repository is named Golden Tier Repository. * The tenant quota is set to 100 GB. * The WAN acceleration is allowed.   |  | | --- | | $repo2 = Get-VBRBackupRepository -Name "Backups Vol2"  $wan = Get-VBRWANAccelerator -Name "WAN 1"  $golden2 = New-VBRCloudTenantResource -Repository $repo2 -RepositoryFriendlyName "Golden Tier Repository" -Quota 100 -EnableWanAccelerator -WanAccelerator $wan |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $repo2 variable. 2. Run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. Specify the Name parameter value. Save the result to the $wan variable. 3. Run the New-VBRCloudTenantResource cmdlet. Specify the following settings:  * Set the $repo2 variable as the Repository parameter value. * Specify the RepositoryFriendlyName parameter value. * Specify the Quota parameter value. * Provide the EnableWanAccelerator parameter. * Set the $wan variable as the WanAccelerator parameter value. * Save the result to the $golden2 variable to be used with other cmdlets. |

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRWANAccelerator](get-vbrwanaccelerator.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
