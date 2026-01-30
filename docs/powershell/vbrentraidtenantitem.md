---
title: "VBREntraIDTenantItem"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrentraidtenantitem.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# VBREntraIDTenantItem


Contains settings of a Microsoft Entra ID item of a tenant.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | String | Item ID. |
| Name | String | Item name. |
| RestorePointId | Guid | ID of the latest restore point where the item is available. |
| RestorePointCreationTime | DateTime | Date and time when the latest restore point where the item is available was created. |

Related Commands

[Get-VBREntraIDTenantItem](get-vbrentraidtenantitem.md)

[Validate-VBREntraIDTenantItem](validate-vbrentraidtenantitem.md)


