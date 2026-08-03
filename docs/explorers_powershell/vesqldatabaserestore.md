---
title: "VESQLDatabaseRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vesqldatabaserestore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VESQLDatabaseRestore


Contains details about a restored PostgreSQL instance.

VESQLDatabaseRestore

| Property | Type | Description |
| JobId | GUID | Job ID. |
| RestorePointId | GUID | Restore point ID. |
| DatabaseName | String | Database name. |
| InstanceName | String | Instance name. |
| ServerName | String | DNS name or IP address of the source server. |
| ToPointInTimeUtc | DateTime | Date and time in the UTC format to which the database will be exported. |
| TargetFolder | String | Destination folder. |
| TargetPath | String[] | Array of target paths. |
| Status | String | Status of the restore operation. Possible values:   * Created * Initializing * Running * Success * Canceling * Canceled * Failed * WaitingForRetry * Completed |
| ErrorMessage | String? | Error or warning message triggered by unexpected conditions during restore. |

Related Commands

* [Start-VESQLDatabaseRestore](start-vesqldatabaserestore.md)
* [Get-VESQLDatabaseRestore](get-vesqldatabaserestore.md)
* [Stop-VESQLDatabaseRestore](stop-vesqldatabaserestore.md)

Page updated 2026-01-29

