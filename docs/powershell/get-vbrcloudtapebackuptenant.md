---
title: "Get-VBRCloudTapeBackupTenant"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcloudtapebackuptenant.html"
last_updated: "3/4/2024"
product_version: "13.0.1.1071"
---

# Get-VBRCloudTapeBackupTenant


Short Description

Returns tenants backups.

Applies to

Product Edition: Enterprise

Requires Cloud Connect license

Syntax

This cmdlet provides parameter sets that allow you to:

* Get tenants backups by the tenant name.

|  |
| --- |
| Get-VBRCloudTapeBackupTenant [-Name <string[]>]  [<CommonParameters>] |

* Get tenant backups by the tenant ID.

|  |
| --- |
| Get-VBRCloudTapeBackupTenant -Id <guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns the array of backups of tenants.

|  |
| --- |
| ![Get-VBRCloudTapeBackupTenant](images/icon_important.webp) Important! |
| You can run this cmdlet from the service provider side only. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of tenant names. The cmdlet will return backups of tenants with these names. | String[] | False | Named | True (ByValue, ByProperty Name) |
| Id | Specifies an array of tenant IDs. The cmdlet will return backups of tenants with the specified IDs. | Guid[] | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

VBRCloudTapeBackupTenant

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Backups of All Tenants

|  |  |
| --- | --- |
| This command gets backups of all tenants.  |  | | --- | | Get-VBRCloudTapeBackupTenant | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Backups of Selected Tenant by Tenant ID

|  |  |
| --- | --- |
| This command gets backups of a tenant with a specific tenant ID.  |  | | --- | | Get-VBRCloudTapeBackupTenant -ID "0fccf7c9-1f90-49de-8bec-53a0697e04ab" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Backups of Selected Tenant by Tenant Name

|  |  |
| --- | --- |
| This command gets backups of a tenant by the tenant name.  |  | | --- | | Get-VBRCloudTapeBackupTenant -Name "New tenant" | |


