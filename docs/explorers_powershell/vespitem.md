---
title: "vespitem"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vespitem.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about a Microsoft SharePoint item.

| Property | Type | Description |
| --- | --- | --- |
| Parent | VESPItem | Parent item. |
| List | [VESPList](vesplist.md) | List where the item is located. |
| Title | String | Item title. |
| HasAttachments | Bool | If True, the item has attachments. |
| Name | String | Item name. |
| CreatedBy | String | User who created the item. |
| CreationTime | DateTime | Date and time when the item was created. |
| ModifiedBy | String | User or application that last modified the file. |
| ModificationTime | DateTime | Date and time when the item was last modified. |
| Version | String | Item version. |
| Type | String | Item type. |
| IsContainer | Bool | If True, the item is a folder. |

Related Commands

[Get-VESPItem](get-vespitem.md)

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
