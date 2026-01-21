---
title: "Delete From Library Job Started"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_124.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Delete From Library Job Started


Sent when a user starts a delete from library job session.

General Information

Event ID: 124

Event message details: Delete from Library job <JobName> has been started by user <UserName>

Severity: Info

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="dd5e025f-7e6b-467a-94ba-c9e7c2911854" |
| JobID | Job ID. | JobID="61fab03f-3065-431f-a2ef-1e4e141fe8e0" |
| JobType | Job type. | JobType="56" |
| Platform | Platform type. | Platform="5" |
| Flags | Defines whether the job was started by a user. | Flags="1" |
| TargetObjectID | Target object ID. | TargetObjectID="00000000-0000-0000-0000-000000000000" |
| TapeIDs | Tape IDs. | TapeIDs="6e2d5920-cede-443f-aabd-e8072dc9f729" |
| OperationSummary | Operation details. | OperationSummary="Tapes to delete from library: HPE009L2" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Delete from Library job 'Delete from Library' has been started by user TECH\user1." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-30T11:08:28.921117+01:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=124 JobSessionID="dd5e025f-7e6b-467a-94ba-c9e7c2911854" JobID="61fab03f-3065-431f-a2ef-1e4e141fe8e0" JobType="56" Platform="5" Flags="1" TargetObjectID="00000000-0000-0000-0000-000000000000" TapeIDs="6e2d5920-cede-443f-aabd-e8072dc9f729" OperationSummary="Tapes to delete from library: HPE009L2" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Delete from Library job 'Delete from Library' has been started by user TECH\user1."] |


