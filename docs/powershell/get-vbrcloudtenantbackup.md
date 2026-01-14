---
title: "Get-VBRCloudTenantBackup"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudtenantbackup.html"
last_updated: "10/6/2025"
product_version: "13.0.1.1071"
---

# Get-VBRCloudTenantBackup

In this article

Short Description

Returns backups of AD tenants and tenants managed by the Service Provider.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get non-encrypted backups by the backup name.

|  |
| --- |
| Get-VBRCloudTenantBackup [-Name <String[]>] [-Tenant <IVBRCloudTenant[]>]  [<CommonParameters>] |

* Get non-encrypted backups by the backup ID.

|  |
| --- |
| Get-VBRCloudTenantBackup [-Id <guid[]>] [-Name <String[]>] [-Tenant <IVBRCloudTenant[]>]  [<CommonParameters>] |

* Get all backups for the tenant account.

|  |
| --- |
| Get-VBRCloudTenantBackup [-All] [-Id <Guid[]>] [-Name <String[]>] [-Tenant <IVBRCloudTenant[]>]  [<CommonParameters>] |

Detailed Description

Returns backups of AD tenants and tenants managed by the Service Provider.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of the job names. The cmdlet will return backups produced with these jobs. | String[] | False | Named | True (ByPropertyName, ByValue) |
| Tenant | Specifies an array of tenant accounts for which you want to get backup files. | Accepts the IVBRCloudTenant[] object. To create this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | False | Named | True (ByPropertyName, ByValue) |
| Id | Specifies an array of the backup IDs. The cmdlet will return backups with these IDs. | Guid[] | False | Named | True (ByPropertyName, ByValue) |
| All | Defines that the cmdlet will return all types of backups: encrypted, non-encrypted, managed and not managed by the Service Provider. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudTenantBackup](vbrcloudtenantbackup.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Non-Encrypted Backups for AD Tenant Accounts

|  |  |
| --- | --- |
| This example shows how to get a list of non-encrypted backups of the ABC Company tenant.  |  | | --- | | $tenant = Get-VBRCloudTenant -Name "ABC Company"  $backupfiles = Get-VBRCloudTenantBackup -Tenant $tenant |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable. 2. Run the Get-VBRCloudTenantBackup cmdlet. Set the $tenant variable as the Tenant parameter value. Save the result to the $backupfiles variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting All Backups for Tenant Account

|  |  |
| --- | --- |
| This example shows how to get a list of all encrypted and non-encrypted backups of the ABC Company tenant.  |  | | --- | | $tenant = Get-VBRCloudTenant -Name "ABC Company"  $allbackups = Get-VBRCloudTenantBackup -All -Tenant $tenant |  Perform the following steps:   1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable. 2. Run the Get-VBRCloudTenantBackup cmdlet. Provide the All parameter. Set the $tenant variable as the Tenant parameter value. Save the result to the $allbackups variable. |

Related Commands

[Get-VBRCloudTenant](get-vbrcloudtenant.md)

Page updated 10/6/2025

Page content applies to build 13.0.1.1071
