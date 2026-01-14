---
title: "vbrexchangerestoresession"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vbrexchangerestoresession.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about a Veeam Explorer for Microsoft Exchange restore session started with a restore point created by Veeam Backup & Replication.

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Restore session ID. |
| StartTime | DateTime | Date and time when the restore session was started. |
| IsRestoreAvailable | Bool | If True, you can restore your data. |
| Audit | ExchangeExtendedAuditWrapper | Audit. |
| IsClosed | Bool | If True, the session has been stopped. |
| Stores | [VEXDatabase](vexdatabase.md) | Path to the Microsoft Exchange database. |

Related Commands

* [Start-VBRExchangeItemRestoreSession](start-vbrexchangeitemrestoresession.md)
* [Get-VBRExchangeItemRestoreSession](get-vbrexchangeitemrestoresession.md)
* [Stop-VBRExchangeItemRestoreSession](stop-vbrexchangeitemrestoresession.md)

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
