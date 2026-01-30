---
title: "Get-VBREntraIDTenantBackup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrentraidtenantbackup.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# Get-VBREntraIDTenantBackup


Short Description

Returns backups of Microsoft Entra ID tenants.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all backups of Entra ID tenants.

|  |
| --- |
| Get-VBREntraIDTenantBackup  [<CommonParameters>] |

* Get backups by their IDs.

|  |
| --- |
| Get-VBREntraIDTenantBackup -Id <Guid[]>  [<CommonParameters>] |

* Get backups by job names.

|  |
| --- |
| Get-VBREntraIDTenantBackup -Name <String[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns backups of Microsoft Entra ID tenants.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of tenant backup IDs. | Guid[] | True | Named | True (ByPropertyName) |
| Name | Specifies an array of job names whose backups you want to get. | String[] | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the array of [VBREntraIDTenantBackup](vbrentraidtenantbackup.md) objects that contain properties of backups.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Backups

|  |  |
| --- | --- |
| This example shows how to get all backups.  |  | | --- | | $tenantBackups = Get-VBREntraIDTenantBackup | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Backup by Job Name

|  |  |
| --- | --- |
| This example shows how to get backups of the Tenant Backup backup job.  |  | | --- | | $tenantBackup = Get-VBREntraIDTenantBackup -Name "Tenant Backup" | |


