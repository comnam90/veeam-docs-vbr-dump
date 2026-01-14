---
title: "vehanarestore"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vehanarestore.html"
last_updated: "8/8/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about a backed-up SAP HANA database.

| Property | Type | Description |
| --- | --- | --- |
| JobId | GUID | Restore job ID. |
| Status | VEHANARestoreStatus | Restore job status. Possible values:   * Created * InProgress * Success * Failed * Cancelled |
| Database | String | Database name. |
| ExceptionMessage | String | Error or warning message triggered by unexpected conditions during restore. |

Related Commands

* [Start-VEHANADatabaseRestore](start-vehanadatabaserestore.md)
* [Get-VEHANADatabaseRestore](get-vehanadatabaserestore.md)
* [Stop-VEHANADatabaseRestore](stop-vehanadatabaserestore.md)
* [Restart-VEHANADatabaseRestore](restart-vehanadatabaserestore.md)

Page updated 8/8/2025

Page content applies to build 13.0.1.1071
