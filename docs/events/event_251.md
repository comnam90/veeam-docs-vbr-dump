---
title: "event_251"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_251.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when a restore task session for Hyper-V virtual machine is finished. For more information, see [Entire VM Restore](https://helpcenter.veeam.com/docs/backup/hyperv/full_recovery.html).

General Information

Event ID: 251

Event message details: Restore for <VmName> has finished with <State> state

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="e54ed5f9-5aea-40e3-9bfb-4e9a464b1907" |
| TaskSessionID | Task session ID. | TaskSessionID="d0c597d6-0294-45f3-abb8-6670235bfd58" |
| Status | Session status ID. Possible values:   * 0 — Success * 2 — Failed * 3 — Warning * 5 — In progress * 6 — Pending | Status="0" |
| SourceHostName | Source host name. | SourceHostName="hv01.tech.local" |
| VmID | Machine reference ID. | VmID="49f7027c-e1b0-4075-bda0-28559129179e" |
| VmName | Machine name. | VmName="Server 03" |
| ServerName | Server name. | ServerName="hv01.tech.local" |
| Location | Location path. | Location="C:\Hyper-V" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Restore for 'Server 03' has finished with Success state." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-20T14:02:20.384033+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=251 JobSessionID="e54ed5f9-5aea-40e3-9bfb-4e9a464b1907" TaskSessionID="d0c597d6-0294-45f3-abb8-6670235bfd58" Status="0" SourceHostName="hv01.tech.local" VmID="49f7027c-e1b0-4075-bda0-28559129179e" VmName="Server 03" ServerName="hv01.tech.local" Location="C:\Hyper-V" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Restore for 'Server 03' has finished with Success state."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
