---
title: "Start-VBRCloudTenantBackupEvacuation"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrcloudtenantbackupevacuation.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Start-VBRCloudTenantBackupEvacuation


Short Description

Starts to migrate tenant data between performance extents.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRCloudTenantBackupEvacuation -SourceExtent <VBRRepositoryExtent> -TargetExtent <VBRRepositoryExtent> -Tenant <IVBRCloudTenant>  [<CommonParameters>] |

Detailed Description

This cmdlet allows to migrate backed-up tenant data between performance extents of a scale-out backup repository. The cmdlet will disable the tenant account while performing the migration from the source performance extent to the target performance extent. After the migration is completed, the cmdlet will enable the tenant account.

If performance extents consist of repositories with [Fast Clone](https://helpcenter.veeam.com/docs/vbr/userguide/backup_repository_block_cloning.html?ver=13) enabled, the migration process uses Fast Clone technology. The backed-up data is not hydrated on relocating.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SourceExtent | Specifies the source performance extent from which you want to migrate the tenant data. | Accepts the [VBRRepositoryExtent](vbrrepositoryextent.md) object. To create this object, run the [Get-VBRRepositoryExtent](get-vbrrepositoryextent.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| TargetExtent | Specifies the target performance extent to which you want to migrate the tenant data. | Accepts the [VBRRepositoryExtent](vbrrepositoryextent.md) object. To create this object, run the [Get-VBRRepositoryExtent](get-vbrrepositoryextent.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Tenant | Specifies the tenant which data you want to migrate. | Accepts the IVBRCloudTenant object. To create this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Migrating Tenant Data Between Performance Extents

This example shows how to migrate the ABC Company tenant data between performance extents of a scale-out backup repository.

|  |
| --- |
| $scaleoutrepository = Get-VBRBackupRepository -Name "Veeam Performance Scale-Out Repository" -ScaleOut  $source = Get-VBRRepositoryExtent -Repository $scaleoutrepository  $target = Get-VBRRepositoryExtent -Repository $scaleoutrepository  $tenant = Get-VBRCloudTenant -Name "ABC Company"  Start-VBRCloudTenantBackupEvacuation -SourceExtent $source[0] -TargetExtent $target[1] -Tenant $tenant |

Perform the following steps:

1. Get the source and target performance extents.

1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Provide the ScaleOut parameter. Save the result to the $scaleoutrepository variable.
2. Run the [Get-VBRRepositoryExtent](get-vbrrepositoryextent.md) cmdlet. Specify the Repository parameter value. Save the result to the $source variable.
3. Run the [Get-VBRRepositoryExtent](get-vbrrepositoryextent.md) cmdlet. Specify the Repository parameter value. Save the result to the $target variable.

The Get-VBRRepositoryExtent cmdlet will return an array of extents. Mind the ordinal number of the necessary extent (in our example, it is the first and the second extents in the array).

1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable.
2. Run the Start-VBRCloudTenantBackupEvacuation cmdlet. Specify the following settings:

* Set the $source[0] variable as the SourceExtent parameter value.
* Set the $target[1] variable as the TargetExtent parameter value.
* Set the $tenant variable as the Tenant parameter value.

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRRepositoryExtent](get-vbrrepositoryextent.md)
* [Get-VBRCloudTenant](get-vbrcloudtenant.md)


