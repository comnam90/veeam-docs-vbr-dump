---
title: "Tape Eject Job Started"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_121.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Tape Eject Job Started


Sent when a user starts a tape eject job session. For more information, see [Ejecting Tapes](https://helpcenter.veeam.com/docs/backup/vsphere/ejecting_tapes.html).

General Information

Event ID: 121

Event message details: Tape Eject job <JobName> has been started by user <UserName>

Severity: Info

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="d87d298a-c4e2-428d-8493-7b535975715d" |
| JobID | Job ID. | JobID="3257e163-8a43-4426-a6f4-cf3acb5345e9" |
| JobType | Job type. | JobType="33" |
| Platform | Platform type. | Platform="5" |
| Flags | Defines whether the job was started by a user. | Flags="1" |
| TargetObjectID | Target object ID. | TargetObjectID="00000000-0000-0000-0000-000000000000" |
| TapeIDs | Tape IDs. | TapeIDs="d85af4ee-38e6-4e57-9ccd-9b02abf56201" |
| OperationSummary | Operation details. | OperationSummary="Tapes to eject: HPE002L2" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description=Tape Eject job 'Tape Eject' has been started by user TECH\user1."" |

Syslog Message Example

|  |
| --- |
| 1 2025-11-30T11:03:07.935655+01:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=121 JobSessionID="d87d298a-c4e2-428d-8493-7b535975715d" JobID="3257e163-8a43-4426-a6f4-cf3acb5345e9" JobType="33" Platform="5" Flags="1" TargetObjectID="00000000-0000-0000-0000-000000000000" TapeIDs="d85af4ee-38e6-4e57-9ccd-9b02abf56201" OperationSummary="Tapes to eject: HPE002L2" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Tape Eject job 'Tape Eject' has been started by user TECH\user1."] |


