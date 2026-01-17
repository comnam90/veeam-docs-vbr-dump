---
title: "VESQLPluginDatabaseFile"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vesqlplugindatabasefile.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---

# VESQLPluginDatabaseFile


Contains details about Microsoft SQL Server database files backed up with Veeam Plug-in for Microsoft SQL Server.

| Property | Type | Description |
| --- | --- | --- |
| Path | String | Path to the database file. |
| LogicalName | String | Logical name of the database file. |
| Type | VESQLPluginDatabaseFileType | Database file type. Possible values:   * Primary * Secondary * Blobs |
| Size | Ulong | File size, in bytes. |

Related Commands

[Get-VESQLPluginDatabaseFile](get-vesqlplugindatabasefile.md)


