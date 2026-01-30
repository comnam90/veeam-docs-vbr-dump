---
title: "VBRApplicationRestorePoint"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrapplicationrestorepoint.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRApplicationRestorePoint


Contains restore point created with VSS-aware image processing enabled.

Properties

| Property | Type | Description |
| --- | --- | --- |
| IsExchange | bool | Indicates if the restore point contains a Microsoft Exchange VM backup (TRUE) or not (FALSE). |
| IsActiveDirectory | bool | Indicates if the restore point contains a Microsoft Active Directory VM backup (TRUE) or not (FALSE). |
| IsSharePoint | bool | Indicates if the restore point contains a Microsoft SharePoint VM backup (TRUE) or not (FALSE). |
| IsSQL | bool | Indicates if the restore point contains a Microsoft SQL Server VM backup (TRUE) or not (FALSE). |
| IsOracle | bool | Indicates if the restore point contains an Oracle VM backup (TRUE) or not (FALSE). |
| CreationTime | DateTime | Date and time of creation of the restore point. |
| Type | [VBRRestorePointType](enums.md#VBRRestorePointType) | Restore point type. |
| IsIndexed | bool | Indicates if the application-aware image processing is enabled (TRUE) or not (FALSE). |
| IsCorrupted | bool | Indicates if the restore point is corrupted (TRUE) or not (FALSE). |
| Name | string | Name of VM in the restore point. |
| Id | GUID | Restore point ID. |

Related Commands

[Get-VBRApplicationRestorePoint](get-vbrapplicationrestorepoint.md)


