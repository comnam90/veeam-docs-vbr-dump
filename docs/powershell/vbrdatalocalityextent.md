---
title: "VBRDataLocalityExtent"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrdatalocalityextent.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRDataLocalityExtent

In this article

Contains scale-out backup repository extent with Data locality policy.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Extent ID.  Extents are not registered in the Veeam database until they are not added to a scale-out repository. The ID of such extent is {00000000-0000-0000-0000-000000000000}. |
| ParentId | GUID | Parent scale-out repository ID.  If the scale-out repository is not created yet, the ID is  {00000000-0000-0000-0000-000000000000}. |
| Repository | CBackupRepository | Backup repository that is converted into the extent. |
| Status | [VBRRepositoryExtentStatus](enums.md#VBRRepositoryExtentStatus) | Extent status. |

Related Commands

* [Get-VBRRepositoryExtent](get-vbrrepositoryextent.md)
* [Set-VBRRepositoryExtent](set-vbrrepositoryextent.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
