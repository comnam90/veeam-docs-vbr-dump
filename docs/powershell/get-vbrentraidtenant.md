---
title: "Get-VBREntraIDTenant"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrentraidtenant.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# Get-VBREntraIDTenant


Short Description

Returns Microsoft Entra ID tenants added to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all tenants added to the backup infrastructure.

|  |
| --- |
| Get-VBREntraIDTenant  [<CommonParameters>] |

* Get tenants by their IDs in the Veeam Backup & Replication backup infrastructure.

|  |
| --- |
| Get-VBREntraIDTenant [-Id <Guid[]>]  [<CommonParameters>] |

* Get tenants by their IDs in the Microsoft Entra ID infrastructure.

|  |
| --- |
| Get-VBREntraIDTenant [-AzureTenantId <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Entra ID tenants added to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of Veeam Backup & Replication tenant IDs.  Note: These are IDs that Veeam Backup & Replication assigns to the tenants after they are added to the backup infrastructure. | Guid[] | False | Named | True (ByPropertyName) |
| AzureTenantId | Specifies an array of Microsoft Entra tenant IDs. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the array of [VBREntraIdTenant](vbrentraidtenant.md) objects that contain settings of tenants.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Tenants

|  |  |
| --- | --- |
| This example shows how to get all tenants added to the backup infrastructure.  |  | | --- | | $tenants = Get-VBREntraIdTenant | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Tenant Using Entra ID

|  |  |
| --- | --- |
| This example shows how to get a tenant using its tenant ID in Entra ID.  |  | | --- | | $tenant = Get-VBREntraIdTenant -AzureTenantId "xxxx" | |


