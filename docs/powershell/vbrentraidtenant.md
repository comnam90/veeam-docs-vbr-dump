---
title: "VBREntraIDTenant"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrentraidtenant.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# VBREntraIDTenant


Contains Microsoft Entra ID tenant options.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | Guid | Tenant ID in Veeam Backup & Replication. |
| Name | String | Tenant name. |
| AzureTenantId | String | Tenant ID in Microsoft Entra ID. |
| Description | String | Tenant description. |
| ApplicationId | String | ID of the application that was used to add the tenant. |
| Region | VBRAzureBlobRegionType | Tenant region. |
| CacheRepository | CBackupRepository | Cache repository used for the tenant. |

Related Commands

* [Add-VBREntraIDTenant](add-vbrentraidtenant.md)
* [Get-VBREntraIDTenant](get-vbrentraidtenant.md)
* [Set-VBREntraIDTenant](set-vbrentraidtenant.md)


