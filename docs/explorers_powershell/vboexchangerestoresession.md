---
title: "vboexchangerestoresession"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vboexchangerestoresession.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about a Veeam Explorer for Microsoft Exchange restore session started with a restore point created by Veeam Backup for Microsoft 365.

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Restore session ID. |
| IsRestoreAvailable | Bool | If True, you can use this restore session to restore your data. |
| Audit | ExchangeExtendedAuditWrapper | Audit. |
| IsClosed | Bool | If True, the session has been stopped. |
| Stores | [VEXDatabase](vexdatabase.md) | Path to the Microsoft Exchange database. |

Related Commands

* [Start-VBOExchangeItemRestoreSession](start-vboexchangeitemrestoresession.md)
* [Get-VBOExchangeItemRestoreSession](get-vboexchangeitemrestoresession.md)
* [Stop-VBOExchangeItemRestoreSession](stop-vboexchangeitemrestoresession.md)

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
