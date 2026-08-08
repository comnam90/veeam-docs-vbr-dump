---
title: "VEADRestoreSessionJob"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/veadrestoresessionjob.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VEADRestoreSessionJob


Contains details about a Veeam Explorer for Microsoft Active Directory restore session.

VEADRestoreSessionJob

| Property | Type | Description |
| Database | [VEADDomain](veaddomain.md) | Backed-up Active Directory domain. Displayed as nds.dit file path. |
| Id | GUID | Restore session ID. |
| StartTime | DateTime | Date and time when the restore session was started. |
| IsClosed | Bool | If True, the session has been stopped. |
| Type | VEADSessionType | Restore session type. Possible values:   * Local * Remote |

Related Commands

* [Start-VEADRestoreSessionJob](start-veadrestoresessionjob.md)
* [Get-VEADRestoreSessionJob](get-veadrestoresessionjob.md)

Page updated 2026-01-30

