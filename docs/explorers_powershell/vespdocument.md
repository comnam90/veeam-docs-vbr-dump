---
title: "VESPDocument"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vespdocument.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about a Microsoft SharePoint document.

| Property | Type | Description |
| --- | --- | --- |
| Parent | VESPDocument | Parent document. |
| DocumentLibrary | [VESPDocumentLibrary](vespdocumentlibrary.md) | Document library where the document is located. |
| Name | String | Document name. |
| CreatedBy | String | User who created the document. |
| CreationTime | DateTime | Date and time when the document was created. |
| ModifiedBy | String | User or application that last modified the file. |
| ModificationTime | DateTime | Date and time when the item was last modified. |
| Version | String | Document version. You can use the [Get-VESPDocumentVersion](get-vespdocumentversion.md) to switch between document versions. |
| Type | String | Document type. |
| IsContainer | Bool | If True, the document is a folder. |

Related Commands

[Get-VESPDocument](get-vespdocument.md)

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
