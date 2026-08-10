---
title: "VEPSQLDatabaseRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vepsqldatabaserestore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VEPSQLDatabaseRestore


Contains details about a restored PostgreSQL database.

VEPSQLDatabaseRestore

| Property | Type | Description |
| Id | GUID | Instance ID. |
| Session | GUID | Restore session ID. |
| RestorePointId | GUID | Restore point ID. |
| ToPointInTimeUTC | DateTime | Date and time in the UTC format of the state as of which the database is restored. |
| ServerName | String | DNS name or IP address of the target server for the restore operation. |
| InstanceName | String | Target instance name. |
| DatabaseName | String | Target database name. |
| Status | String | Status of the restore operation. |

Related Commands

* [Start-VEPSQLDatabaseRestore](start-vepsqldatabaserestore.md)
* [Get-VEPSQLDatabaseRestore](get-vepsqldatabaserestore.md)
* [Stop-VEPSQLDatabaseRestore](stop-vepsqldatabaserestore.md)

Page updated 2026-03-10

