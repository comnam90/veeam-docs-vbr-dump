---
title: "VESQLDatabaseExport"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vesqldatabaseexport.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VESQLDatabaseExport


Contains details about the export process for a Microsoft SQL Server database.

VESQLDatabaseExport

| Property | Type | Description |
| JobId | GUID | Job ID. |
| RestorePointId | GUID | Restore point ID. |
| TargetHost | String | DNS name or IP address of the target server. |
| DatabaseName | String | Database name. |
| InstanceName | String | Instance name. |
| ServerName | String | DNS name or IP address of the source server. |
| ToPointInTimeUtc | DateTime | Date and time in the UTC format to which the database will be exported. |
| Status | String | Status of the restore operation. Possible values:   * Created * Initializing * Running * Success * Canceling * Canceled * Failed * WaitingForRetry * Completed |
| ErrorMessage | String? | Error or warning message triggered by unexpected conditions during restore. |

Related Commands

* [Start-VESQLDatabaseExport](start-vesqldatabaseexport.md)
* [Get-VESQLDatabaseExport](get-vesqldatabaseexport.md)
* [Stop-VESQLDatabaseExport](stop-vesqldatabaseexport.md)

Page updated 2026-01-29

