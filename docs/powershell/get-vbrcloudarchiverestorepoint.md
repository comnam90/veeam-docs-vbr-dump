---
title: "Get-VBRCloudArchiveRestorePoint"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudarchiverestorepoint.html"
last_updated: "6/18/2024"
product_version: "13.0.1.1071"
---

# Get-VBRCloudArchiveRestorePoint

In this article

Short Description

Returns restore points of tenant backups located in the archive tier.

Applies to

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRCloudArchiveRestorePoint -Tenant <VBRCloudTenant> [-Id <guid>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns restore points of tenant backups located in the archive tier.

The cloud provider needs to run this cmdlet when a tenant wants to restore backups stored in the archive extent of the scale-out backup repository. Since the tenant is not able to restore data on his side, he needs to contact the cloud provider and specify an ID of the restore point for backups that he wants to restore.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Tenant | Specifies a tenant whose data you want to restore. | Accepts the [VBRCloudTenant](vbrcloudtenant.md) object. To create this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Id | Specifies a restore point ID of tenant backups that you want to restore. | Guid | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCloudArchiveRestorePoint object that contains a restore point of tenant backups located in the archive tier.

Examples

Getting Restore Point of Tenant Backup Stored in Archive Tier

This example shows how to get the 3e57a915-2755-4297-be14-deddb8564ca9 restore point of the ABC Company tenant.

|  |
| --- |
| $tenant = Get-VBRCloudTenant -Name "ABC Company"  Get-VBRCloudArchiveRestorePoint -Tenant $tenant -Id "3e57a915-2755-4297-be14-deddb8564ca9" |

Perform the following steps:

1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable.

1. Run the Get-VBRCloudArchiveRestorePoint cmdlet. Set the $tenant variable as the Tenant parameter value. Specify the Id parameter value.

Related Commands

[Get-VBRCloudTenant](get-vbrcloudtenant.md)

Page updated 6/18/2024

Page content applies to build 13.0.1.1071
