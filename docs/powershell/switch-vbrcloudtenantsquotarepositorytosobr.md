---
title: "Switch-VBRCloudTenantsQuotaRepositoryToSOBR"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/switch-vbrcloudtenantsquotarepositorytosobr.html"
last_updated: "7/29/2025"
product_version: "13.0.1.1071"
---

# Switch-VBRCloudTenantsQuotaRepositoryToSOBR


Short Description

Switches tenant quotas on the cloud repository to a scale-out backup repository.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a cloud provider license.

Syntax

|  |
| --- |
| Switch-VBRCloudTenantsQuotaRepositoryToSOBR -Resource <VBRCloudTenantResource> -ScaleOutBackupRepository <VBRScaleOutBackupRepository>  [-Tenants <IVBRCloudTenant[]>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet switches tenant quotas on the cloud repository to a scale-out backup repository. You can use this cmdlet if you want to move tenant backup data to a scale-out backup repository used as a cloud repository.

Consider the following:

* The cmdlet does not copy the actual backup data from an original cloud repository to a new cloud repository. Instead, it creates folders for tenant data on extents of the scale-out backup repository used as a cloud repository, copies backup metadata to these folders and prompts the user to copy backup files to these folders as well.

Note that either all folders or no folders that are being migrated must exist on the scale-out backup repository. If some tenant folders already exist on the scale-out backup repository, while other folders are missing, the migration process will fail.

* Migration of tenant data from and to object storage used as a cloud repository is not supported.
* Migration to a scale-out backup repository is not possible if at least one extent is in the maintenance mode.
* Names of folders with tenant backup data on the cloud repository must not contain special characters (for example, \/`~,!?#$&\*|{}[];"<>) and non-ASCII characters.
* During migration, tenant accounts will be automatically disabled. The service provider must enable the disabled accounts manually once the migration process is completed.
* All subtenants are migrated together with the tenant, it is not possible to migrate only specific subtenants.м
* The tenant must not have more than 1 quota assigned.

Parameters

| Parameter | Description | Type | Required | Position | Accept | Accept Wildcard Characters |
| --- | --- | --- | --- | --- | --- | --- |
| Resource | Specifies the object that contains the tenant backup resource. The cmdlet will switch this tenant backup resource to a scale-out backup repository. | Accepts the [VBRCloudTenantResource](vbrcloudtenantresource.md) object. To create this object, run the [New-VBRCloudTenantResource](new-vbrcloudtenantresource.md) cmdlet and provide the ScaleOut parameter. | True | Named | True (ByValue,  ByPropertyName) | False |
| ScaleOutBackupRepository | Specifies the scale-out backup repository where you want to create cloud repository quota for a tenant account. | Accepts the [VBRScaleOutBackupRepository](vbrscaleoutbackuprepository.md) object. To create this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet and provide the ScaleOut parameter. | True | Named | True (ByValue,  ByPropertyName) | False |
| Tenants | Specifies the array of tenant accounts for which you want to create cloud repository quota on a scale-out backup repository. | Accepts the IVBRCloudTenant object. To create this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | False | Named | True (ByValue,  ByPropertyName) | False |
| Force | Defines that the cmdlet will switch tenant quotas on the cloud repository to a scale-out backup repository without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Switching Tenant Quota on Cloud Repository to Scale-Out Backup Repository

This example shows how to switch tenant quota on the cloud repository to a scale-out backup repository.

|  |
| --- |
| $repository = Get-VBRBackupRepository -ScaleOut -Name "Veeam Scale-Out Backup Repository"  $tenant = Get-VBRCloudTenant -Name "ABC Company"  Switch-VBRCloudTenantsQuotaRepositoryToSOBR -ScaleOutBackupRepository $repository -Tenants $tenant |

Perform the following steps:

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Provide the ScaleOut parameter. Specify the Name parameter value. Save the result to the $repository variable.
2. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable.
3. Run the Switch-VBRCloudTenantsQuotaRepositoryToSOBR cmdlet. Specify the following settings:

* Set the $repository variable as the ScaleOutBackupRepository parameter value.
* Set the $tenant variable as the Tenant parameter value.

1. The cmdlet will prompt you to perform the following operations:

1. Confirm that the specified tenant accounts will be disabled.
2. Copy tenant backup files to the folders that the cmdlet has created on the scale-out backup repository, and then confirm that the backup files have been copied.
3. Confirm that the cmdlet will update tenant backups and cloud repository settings for the tenant account.
4. Confirm that the cmdlet will rescan the new cloud repository.

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRCloudTenant](get-vbrcloudtenant.md)


