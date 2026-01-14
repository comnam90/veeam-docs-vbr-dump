---
title: "event_119"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_119.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when a user starts a tape export job session. For more information, see [Exporting Tapes](https://helpcenter.veeam.com/docs/backup/vsphere/importing_exporting_tape_media.html).

General Information

Event ID: 119

Event message details: Tape Export job <JobName> has been started by user <UserName>

Severity: Info

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="02532b59-4908-44df-9350-bf184faccf5a" |
| JobID | Job ID. | JobID="a66e65ba-a34b-4829-8a62-9c7ad2a91df0" |
| JobType | Job type. | JobType="34" |
| Platform | Platform type. | Platform="5" |
| Flags | Defines whether the job was started by a user. | Flags="1" |
| TargetObjectID | Target object ID. | TargetObjectID="00000000-0000-0000-0000-000000000000" |
| TapeIDs | Tape IDs. | TapeIDs="6e2d5920-cede-443f-aabd-e8072dc9f729" |
| OperationSummary | Operation details. | OperationSummary="Tapes to export: HPE009L2" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Tape Export job 'Tape Export' has been started by user TECH\user1." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-30T11:02:49.813348+01:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=119 JobSessionID="02532b59-4908-44df-9350-bf184faccf5a" JobID="a66e65ba-a34b-4829-8a62-9c7ad2a91df0" JobType="34" Platform="5" Flags="1" TargetObjectID="00000000-0000-0000-0000-000000000000" TapeIDs="6e2d5920-cede-443f-aabd-e8072dc9f729" OperationSummary="Tapes to export: HPE009L2" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Tape Export job 'Tape Export' has been started by user TECH\user1."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
