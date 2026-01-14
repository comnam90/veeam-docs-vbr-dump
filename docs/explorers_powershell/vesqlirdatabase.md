---
title: "vesqlirdatabase"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vesqlirdatabase.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about a Microsoft SQL Server database published during an instant recovery session.

| Property | Type | Description |
| --- | --- | --- |
| Session | GUID | Restore session ID. |
| RestorePoint | GUID | Restore point ID. |
| DatabaseName | String | Name of the database on the target server. |
| ServerName | String | DNS name or IP address of the target server. |
| InstanceName | String | Name of the target instance. |
| ToPointInTimeUtc | DateTime | Date and time in the UTC format of the state as of which the database is recovered. |
| TargetFolder | String | Target folder for the database files. |
| FileStatus | String | Recovery status of the file. |
| TargetPath | String[] | Target paths for the database files. |
| Status | String | Status of the instant recovery operation. |
| SwitchOverOptions | [VESQLIRSwitchOverOptions](vesqlirswitchoveroptions.md) | Switchover options for the instant recovery operation. |

Related Commands

* [Restore-VESQLIRDatabase](restore-vesqlirdatabase.md)
* [Get-VESQLIRDatabase](get-vesqlirdatabase.md)
* [Switch-VESQLIRDatabase](switch-vesqlirdatabase.md)
* [Stop-VESQLInstantRecovery](stop-vesqlinstantrecovery.md)

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
