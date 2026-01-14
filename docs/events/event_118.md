---
title: "event_118"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_118.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when a user starts a tape verification job session. For more information, see [Verifying Tapes](https://helpcenter.veeam.com/docs/backup/vsphere/verifying_tapes.html).

General Information

Event ID: 118

Event message details: Validate session has been initiated by <UserName>

Severity: Info

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Description. | JobSessionID="6913f76f-4b00-470b-b2ce-badf2129c2f0" |
| RestoreType | Restore type. | RestoreType="0" |
| InitiatorName | Name of the user who performed an operation. | InitiatorName="TECH\user1" |
| Platform | Platform type. | Platform="5" |
| TargetObjectID | Target object ID. | TargetObject="00000000-0000-0000-0000-000000000000" |
| SourceObjects | Source object IDs. | SourceObjects="b226f493-92ee-4b0e-b7b9-3590cec4ae1d" |
| ExtraData | Operation details. | ExtraData="Tapes to validate: WRM000LS" |
| SourceType | Job source type. | SourceType="6" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Validate session has been initiated by 'TECH\user1'." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-30T10:59:11.688200+01:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=118 JobSessionID="6913f76f-4b00-470b-b2ce-badf2129c2f0" RestoreType="0" InitiatorName="TECH\user1" Platform="5" TargetObjectID="00000000-0000-0000-0000-000000000000" SourceObjects="b226f493-92ee-4b0e-b7b9-3590cec4ae1d" ExtraData="Tapes to validate: WRM000LS" SourceType="6" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Validate session has been initiated by 'TECH\user1'."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
