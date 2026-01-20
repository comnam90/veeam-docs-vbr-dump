---
title: "Library Discovery Job Started"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_125.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Library Discovery Job Started


Sent when a user starts a library discovery job session. For more information, see [Inventorying Tapes](https://helpcenter.veeam.com/docs/backup/vsphere/inventoring_tapes.html).

General Information

Event ID: 125

Event message details: Tape Library Discovery job <JobName> has been started by user <UserName>

Severity: Info

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="85d54fa0-620f-42d0-8a56-ec9a87e858c2" |
| JobID | Job ID. | JobID="4a9c5b19-283c-47a7-8179-103988a1aeec" |
| JobType | Job type. | JobType="37" |
| Platform | Platform type. | Platform="5" |
| Flags | Defines whether the job was started by a user. | Flags="1" |
| TargetObjectID | Target object ID. | TargetObjectID="00000000-0000-0000-0000-000000000000" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Tape Library Discovery job 'Tape Library Discovery' has been started by user TECH\user1." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-30T11:16:32.762154+01:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=125 JobSessionID="85d54fa0-620f-42d0-8a56-ec9a87e858c2" JobID="4a9c5b19-283c-47a7-8179-103988a1aeec" JobType="37" Platform="5" Flags="1" TargetObjectID="00000000-0000-0000-0000-000000000000" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Tape Library Discovery job 'Tape Library Discovery' has been started by user TECH\user1."] |


