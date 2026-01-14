---
title: "event_122"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_122.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when a user starts a mark tape as free job session. For more information, see [Marking Tapes as Free](https://helpcenter.veeam.com/docs/backup/vsphere/marking_tapes_as_free.html).

General Information

Event ID: 122

Event message details: Mark as Free job <JobName> has been started by user <UserName>

Severity: Info

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="e905fe5d-72fb-4d1c-beff-b9eee2f9861b" |
| JobID | Job ID. | JobID="af8071ed-2ce4-4cdd-93a5-244c18364c48" |
| JobType | Job type. | JobType="55" |
| Platform | Platform type. | Platform="5" |
| Flags | Defines whether the job was started by a user. | Flags="1" |
| TargetObjectID | Target object ID. | TargetObjectID="00000000-0000-0000-0000-000000000000" |
| TapeIDs | Tape IDs. | TapeIDs="9c401c8c-36f7-499a-b420-b913186d5a5e" |
| OperationSummary | Operation details. | OperationSummary="Tapes to mark as free: HPE005L2" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Mark as Free job 'Mark as Free' has been started by user TECH\user1." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-30T11:08:11.312736+01:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=122 JobSessionID="e905fe5d-72fb-4d1c-beff-b9eee2f9861b" JobID="af8071ed-2ce4-4cdd-93a5-244c18364c48" JobType="55" Platform="5" Flags="1" TargetObjectID="00000000-0000-0000-0000-000000000000" TapeIDs="9c401c8c-36f7-499a-b420-b913186d5a5e" OperationSummary="Tapes to mark as free: HPE005L2" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Mark as Free job 'Mark as Free' has been started by user TECH\user1."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
