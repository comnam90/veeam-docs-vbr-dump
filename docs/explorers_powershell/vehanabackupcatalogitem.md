---
title: "VEHANABackupCatalogItem"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vehanabackupcatalogitem.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains backup catalog items for a specific SAP HANA database.

| Property | Type | Description |
| --- | --- | --- |
| Id | Long | Backup ID. |
| StartTimeUTC | DateTime | Backup creation time. |
| Size | Long | Backup size in bytes. |
| ExternalBackupIds | String[] | Array of external backup IDs (EBIDs). |
| Database | [VEHANADatabase](vehanadatabase.md) | Backed-up SAP HANA database. |

Related Commands

[Get-VEHANABackupCatalogItem](get-vehanabackupcatalogitem.md)

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
