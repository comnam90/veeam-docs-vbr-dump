---
title: "Set-VBRCloudTenantResource"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcloudtenantresource.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Set-VBRCloudTenantResource

In this article

Short Description

Modifies tenants backup resources settings.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRCloudTenantResource -CloudTenantResource <VBRCloudTenantResource> [-Repository <CBackupRepository>] [-RepositoryFriendlyName <String>] [-Quota <int64>] [-EnableWanAccelerator] [-WanAccelerator <CWanAccelerator>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the [VBRCloudTenantResource](vbrcloudtenantresource.md) object containing the backup resources for a tenant.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| CloudTenantResource | Specifies the cloud account tenant quota settings you want to modify. | Accepts the [VBRCloudTenantResource](vbrcloudtenantresource.md) object. To get this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet and use the resources parameter. | True | Named | False |
| Repository | Specifies the backup repository in your backup infrastructure you want to expose to the tenant.  You can specify simple or scale-out backup repositories.  You cannot specify cloud repositories or individual scale-out repositories extents. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | True | Named | False |
| RepositoryFriendlyName | Specifies a name for the cloud repository you want to present to the tenant. The name you enter will be displayed in the list of backup repositories at tenant’s side. | String | True | Named | False |
| Quota | Specifies the amount of space you want to allocate to the tenant on the selected backup repository.  Permitted value: 1 to 2097151  (GB). | Int64 | True | Named | False |
| EnableWanAccelerator | Enables the option to use WAN accelerators for backup jobs to cloud repositories.  Use the WanAccelerator parameter to set the WAN accelerator. | SwitchParameter | False | Named | False |
| WanAccelerator | Specifies the WAN accelerator for the EnableWanAccelerator parameter. | Accepts the [CWanAccelerator](cwanaccelerator.md) object. To get this object, run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudTenantResource](vbrcloudtenantresource.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Changing Backup Repository Quota of Tenant

|  |  |
| --- | --- |
| This example shows how to change the backup repository quota of a tenant.  |  | | --- | | $tenant = Get-VBRCloudTenant -Name "ABC Company"  $resources = $tenant.resources[0]  $newquota = Set-VBRCloudTenantResource -CloudTenantResource $resources -Quota 20  Set-VBRCloudTenant -CloudTenant $tenant -Resource $newquota |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save it to the $tenant variable. 2. Get the array of quotas assigned to the tenant. Select the first quota from the list. Save the result to the $resources variable. 3. Run the Set-VBRCloudTenantResource cmdlet. Set the $resources variable as the CloudTenantResource parameter value. Specify the Quota parameter value. Save the result to the $newquota variable. 4. Run the [Set-VBRCloudTenant](set-vbrcloudtenant.md) cmdlet to apply the new resources to the tenant. Set the $tenant variable as the CloudTenant parameter value. Set the $newquota variable as the Resource parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Enabling WAN Acceleration for Tenant

|  |  |
| --- | --- |
| This example shows how to enable WAN acceleration for a tenant.  |  | | --- | | $tenant = Get-VBRCloudTenant -Name "ABC Company"  $resources = $tenant.resources[0]  $wan = Get-VBRWANAccelerator -Name "Columbus WAN"  $newresources = Set-VBRCloudTenantResource -CloudTenantResource $resources -EnableWanAccelerator -WanAccelerator $wan  Set-VBRCloudTenant -CloudTenant $tenant -Resource $newresources |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save it to the $tenant variable. 2. Get the array of resources assigned to the tenant. Select the first item from the list. Save the result to the $resources variable. 3. Run the [Get-VBRWANAccelerator](get-vbrwanaccelerator.md) cmdlet. Specify the Name parameter value. Save it to the $wan variable. 4. Run the Set-VBRCloudTenantResource cmdlet. Set the $resources variable as the CloudTenantResource parameter value. Provide the EnableWanAccelerator parameter. Set the $wan variable as the WanAccelerator parameter value.  Save the results to the $newresources variable. 5. Run the [Set-VBRCloudTenant](set-vbrcloudtenant.md) cmdlet to apply the new resources to the tenant. Set the $tenant variable as the CloudTenant parameter value. Set the $newresources variable as the Resource parameter value. |

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRWANAccelerator](get-vbrwanaccelerator.md)
* [Set-VBRCloudTenant](set-vbrcloudtenant.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
