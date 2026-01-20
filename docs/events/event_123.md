---
title: "Move To Media Pool Job Started"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_123.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Move To Media Pool Job Started


Sent when a user starts a move to media pool job session. For more information, see [Moving Tapes to Another Media Pool](https://helpcenter.veeam.com/docs/backup/vsphere/moving_tapes_to_custom_pool.html).

General Information

Event ID: 123

Event message details: Move to Media Pool job <JobName> has been started by user <UserName>

Severity: Info

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="7f1ffcb6-698a-4c42-b8b2-c2f518a5d620" |
| JobID | Job ID. | JobID="bc6e8331-8781-4fc7-85ec-9dd5c7687f3a" |
| JobType | Job type. | JobType="57" |
| Platform | Platform type. | Platform="5" |
| Flags | Defines whether the job was started by a user. | Flags="1" |
| TargetMediaPoolID | Target media pool ID. | TargetMediaPoolID="3730b44e-ce27-405b-ac31-d065294746ca" |
| TapeIDs | Tape IDs. | TapeIDs="02fe017d-1e14-4711-85ba-cac8d53c7ec5" |
| OperationSummary | Operation details. | OperationSummary="Tapes to move: HPE008L2; target pool: HPE - Standard Pool" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Move to Media Pool job 'Move to Media Pool' has been started by user TECH\user1." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-30T11:08:20.412346+01:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=123 JobSessionID="7f1ffcb6-698a-4c42-b8b2-c2f518a5d620" JobID="bc6e8331-8781-4fc7-85ec-9dd5c7687f3a" JobType="57" Platform="5" Flags="1" TargetMediaPoolID="3730b44e-ce27-405b-ac31-d065294746ca" TapeIDs="02fe017d-1e14-4711-85ba-cac8d53c7ec5" OperationSummary="Tapes to move: HPE008L2; target pool: HPE - Standard Pool" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Move to Media Pool job 'Move to Media Pool' has been started by user TECH\user1."] |


