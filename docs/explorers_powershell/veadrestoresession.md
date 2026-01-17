---
title: "VEADRestoreSession"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/veadrestoresession.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about a Veeam Explorer for Microsoft Active Directory restore session.

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Restore session ID. |
| StartTime | DateTime | Date and time when the restore session was started. |
| IsClosed | Bool | If True, the session has been stopped. |
| Database | [VEADDomain](veaddomain.md) | Backed-up Active Directory domain. Displayed as nds.dit file path. |

Related Commands

* [Start-VEADRestoreSession](start-veadrestoresession.md)
* [Get-VEADRestoreSession](get-veadrestoresession.md)
* [Stop-VEADRestoreSession](stop-veadrestoresession.md)

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
