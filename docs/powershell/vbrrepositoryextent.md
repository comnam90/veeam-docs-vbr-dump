---
title: "VBRRepositoryExtent"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrrepositoryextent.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRRepositoryExtent


Contains scale-out backup repository extent.

Extended by:

* [VBRDataLocalityExtent](vbrdatalocalityextent.md)
* [VBRPerformanceExtent](vbrperformanceextent.md)

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Unique identifier of an extent.  Extents are not registered in the Veeam database until they are not added to a scale-out repository.  The ID of such extent is {00000000-0000-0000-0000-000000000000}. You cannot get such objects with [Get-VBRRepositoryExtent](get-vbrrepositoryextent.md). |
| ParentId | GUID | Unique identifier of the parent scale-out repository.  If the scale-out repository is not created yet, the ID is  {00000000-0000-0000-0000-000000000000}. |
| Repository | CBackupRepository | The backup repository that is converted into the extent. |
| Status | [VBRRepositoryExtentStatus](enums.md#VBRRepositoryExtentStatus) | Extent status. |


