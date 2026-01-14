---
title: "event_198"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_198.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when a tape verification job session is finished. For more information, see [Verifying Tapes](https://helpcenter.veeam.com/docs/backup/vsphere/verifying_tapes.html).

General Information

Event ID: 198

Event message details: The validate session has finished with <State> state

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="6913f76f-4b00-470b-b2ce-badf2129c2f0" |
| Result | Result ID. Possible values:   * 0 — Success * 1 — Warning * 2 — Failed | JobResult="0" |
| SourceType | Job source type. | SourceType="6" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="The validate session has finished with Success state." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-30T10:59:15.659797+01:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=198 JobSessionID="6913f76f-4b00-470b-b2ce-badf2129c2f0" Result="0" SourceType="6" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="The validate session has finished with Success state."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
