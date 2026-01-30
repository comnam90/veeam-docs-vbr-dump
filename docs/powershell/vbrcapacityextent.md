---
title: "VBRCapacityExtent"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrcapacityextent.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRCapacityExtent


Contains capacity extent added to a scale-out backup repository.

| Property | Type | Description |
| --- | --- | --- |
| ParentId | GUID | Unique identifier of the parent scale-out repository. |
| Repository | VBRObjectStorageRepository | The backup repository the extent is added to. |
| Status | [VBRCapacityExtentStatus](enums.md#VBRCapacityExtentStatus) | Extent status. |

Related Commands

[Get-VBRCapacityExtent](get-vbrcapacityextent.md)


