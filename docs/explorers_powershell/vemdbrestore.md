---
title: "VEMDBRestore"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vemdbrestore.html"
last_updated: "7/29/2025"
product_version: "13.0.1.1071"
---

# VEMDBRestore


Contains details about a Veeam Explorer for MongoDB restore job.

| Property | Type | Description |
| --- | --- | --- |
| JobId | GUID | Restore job ID. |
| Status | String | Restore job status. Possible values:   * Starting * Running * Success * Cancelling * Cancelled * Failed |
| ExceptionMessage | String | Error or warning message triggered by unexpected conditions during restore. |

Related Commands

* [Start-VEMDBDataRestore](start-vemdbdatarestore.md)
* [Get-VEMDBDataRestore](get-vemdbdatarestore.md)
* [Stop-VEMDBDataRestore](stop-vemdbdatarestore.md)


