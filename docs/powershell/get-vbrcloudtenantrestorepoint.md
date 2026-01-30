---
title: "Get-VBRCloudTenantRestorePoint"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudtenantrestorepoint.html"
last_updated: "2/29/2024"
product_version: "13.0.1.1071"
---

# Get-VBRCloudTenantRestorePoint


Short Description

Returns restore points of non-encrypted backups for AD tenants and tenants managed by the Service Provider.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get restore points of non-encrypted backup for AD tenants and tenants managed by the Service Provider by the job name.

|  |
| --- |
| Get-VBRCloudTenantRestorePoint [-Name <String[]>] [-Backup <VBRCloudTenantBackup[]>]  [<CommonParameters>] |

* Get restore points of non-encrypted backup for AD tenants and tenants managed by the Service Provider by restore point ID.

|  |
| --- |
| Get-VBRCloudTenantRestorePoint [-Id <Guid[]>] [-Name <String[]>] [-Backup <VBRCloudTenantBackup[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns restore points of non-encrypted backups for AD tenants and tenants managed by the Service Provider. You can get the following types of restore points:

* All restore points.
* Restore points by their ID.
* Restore points by a VM name.
* Restore points for specific backups.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of the VM names. The cmdlet will return restore points for these VMs. | String[] | False | Named | True (ByValue, ByPropertyName) |
| Backup | Specifies the array of non-encrypted tenant backups. The cmdlet will return restore points of these backups. | Accepts the VBRCloudTenantBackup[] object. To get this object, run the [Get-VBRCloudTenantBackup](get-vbrcloudtenantbackup.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |
| Id | Specifies an array of the backup IDs. The cmdlet will return backups with these IDs. | Guid[] | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCloudTenantRestorePoint object that contains restore points of non-encrypted backups for AD tenants and tenants managed by the Service Provider.

Examples

Getting Restore Points of Non-Encrypted Backups for AD Tenants and Tenants Managed by Service Provider

This command returns all the restore points of non-encrypted backups for AD tenants and tenants managed by the Service Provider.

|  |
| --- |
| Get-VBRCloudTenantRestorePoint |


