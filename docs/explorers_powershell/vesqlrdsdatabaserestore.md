---
title: "VESQLRDSDatabaseRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vesqlrdsdatabaserestore.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VESQLRDSDatabaseRestore


Contains details about the restore operation of a backed-up Microsoft SQL Server database running on Amazon RDS.

VESQLRDSDatabaseRestore

| Property | Type | Description |
| JobId | GUID | Job ID. |
| Status | VESQLRDSRestoreStatus | Status of the restore operation. Possible values:   * Created * Initializing * Running * Success * Canceling * Canceled * Failed * WaitingForRetry * Completed |
| DatabaseName | String | Target database name. |
| SqlServerName | String | Target server name |
| ErrorMessage | String? | Error or warning message triggered by unexpected conditions during restore. |

Related Commands

* [Start-VESQLRDSDatabaseRestore](start-vesqlrdsdatabaserestore.md)
* [Get-VESQLRDSDatabaseRestore](get-vesqlrdsdatabaserestore.md)
* [Stop-VESQLRDSDatabaseRestore](stop-vesqlrdsdatabaserestore.md)

Page updated 2026-01-27

