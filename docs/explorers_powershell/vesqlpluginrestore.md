---
title: "vesqlpluginrestore"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vesqlpluginrestore.html"
last_updated: "11/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about the restore operation of a database backed up with Veeam Plug-in for Microsoft SQL Server.

| Property | Type | Description |
| --- | --- | --- |
| JobId | GUID | Job ID. |
| Status | VESQLPluginRestoreStatus | Status of the restore operation. Possible values:   * Created * Initializing * Running * Success * Canceling * Canceled * Failed * WaitingForRetry * Completed |
| ExceptionMessage | String | Error or warning message triggered by unexpected conditions during restore. |

Related Commands

* [Start-VESQLPluginDatabaseRestore](start-vesqlplugindatabaserestore.md)
* [Get-VESQLPluginDatabaseRestore](get-vesqlplugindatabaserestore.md)
* [Stop-VESQLPluginDatabaseRestore](stop-vesqlplugindatabaserestore.md)

Page updated 11/10/2025

Page content applies to build 13.0.1.1071
