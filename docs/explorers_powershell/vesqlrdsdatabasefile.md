---
title: "VESQLRDSDatabaseFile"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vesqlrdsdatabasefile.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VESQLRDSDatabaseFile


Contains details about database files for a backed-up Microsoft SQL Server database running on Amazon RDS.

VESQLRDSDatabaseFile

| Property | Type | Description |
| Path | String | Path to the database file. |
| LogicalName | String | Logical name of the database file. |
| Type | VESQLRDSDatabaseFileType | Database file type. Possible values:   * Primary * Secondary * Blobs |
| Size | Ulong | File size, in bytes. |

Related Commands

[Get-VESQLRDSDatabaseFile](get-vesqlrdsdatabasefile.md)

Page updated 2026-01-29

