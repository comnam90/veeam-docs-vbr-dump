---
title: "VEHANASystem"
product: "vbr"
doc_type: "explorers_powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/explorers_powershell/vehanasystem.html"
last_updated: "7/10/2025"
product_version: "13.0.1.1071"
---

# VEHANASystem


Contains details about a backed-up SAP HANA system.

| Property | Type | Description |
| --- | --- | --- |
| Name | GUID | System name. |
| IsDistributed | Bool | If True, the SAP HANA system is distributed across multiple hosts. |
| VersionInfo | String | SAP HANA version. |
| Hosts | [VEHANAHost](vehanahost.md)[] | Array of servers that host the SAP HANA system. |
| Session | [VEHANARestoreSession](vehanarestoresession.md) | Restore session started to restore SAP HANA data. |
| BiosUid | GUID[] | Array of BIOS UUIDs for each host. |

Related Commands

[Get-VEHANASystem](get-vehanasystem.md)


