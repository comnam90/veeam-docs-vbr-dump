---
title: "VEHANARestoreActionLogItem"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vehanarestoreactionlogitem.html"
last_updated: "9/17/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about a backed-up SAP HANA database. Note that "?" indicates that the property accepts zero values.

| Property | Type | Description |
| --- | --- | --- |
| Id | Int | Action log item ID. |
| RecoveryStage | VEHANARestoreJobActionLogItemRecoveryStage | Stage of the restore operation. Possible values:   * RestoreCancelling * RestoreCancelled * DatabaseCreating * DatabaseCreated * Start * Resume * DatabaseRecovery * DatabaseStopping * DatabaseStopped * DatabaseStarting * SystemStopping * SystemStopped * SystemStarting |
| ServiceName | String | SAP HANA service name. |
| Port | Int? | Used port. |
| Status | VEHANARestoreJobActionLogItemStatus | Action log item status. Possible values:   * Running * Warning * Error * Success * Cancel |
| StartTime | DateTime | Start time of the restore operation. |
| Duration | TimeSpan | Elapsed time of the restore operation. |
| Phase | String | Restore phase. |
| MaxProgress | Long? | Value indicating a completed restore operation. By default, this value is 1. |
| CurrentProgress | Long? | Value indicating current progress of the restore operation. When the value reaches 1, the restore job is completed. |
| ErrorMessage | String | Error message displayed in case of unsuccessful restore operation. |

Related Commands

[Get-VEHANARestoreJobActionLogItems](get-vehanarestorejobactionlogitems.md)

Page updated 9/17/2025

Page content applies to build 13.0.1.1071
