---
title: "VEPSQLInstanceInstantRecovery"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vepsqlinstanceinstantrecovery.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---


In this article

Contains details about an PostgreSQL database published during an instant recovery session.

| Property | Type | Description |
| --- | --- | --- |
| Session | GUID | Restore session ID. |
| RestorePointID | GUID | Restore point ID. |
| ToPointInTimeUtc | DateTime | Date and time in the UTC format of the state to which the instance is recovered. |
| ServerName | String | DNS name or IP address of the target server. |
| InstanceName | String | Name of the instance on the target server. |
| DataDirectory | String | Data directory for the published instance. |
| Status | String | Status of the instant recovery operation. |
| SwitchOverOptions | [VEPSQLIRSwitchOverOptions](vepsqlirswitchoveroptions.md) | Switchover options for the instant recovery operation. |

Related Commands

* [Start-VEPSQLInstanceInstantRecovery](start-vepsqlinstanceinstantrecovery.md)
* [Get-VEPSQLInstanceInstantRecovery](get-vepsqlinstanceinstantrecovery.md)
* [Switch-VEPSQLInstanceInstantRecovery](switch-vepsqlinstanceinstantrecovery.md)
* [Restart-VEPSQLInstanceInstantRecovery](restart-vepsqlinstanceinstantrecovery.md)
* [Stop-VEPSQLInstanceInstantRecovery](stop-vepsqlinstanceinstantrecovery.md)

Page updated 7/10/2025

Page content applies to build 13.0.1.1071
