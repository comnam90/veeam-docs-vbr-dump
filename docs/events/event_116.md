---
title: "Tape Inventorying Job Started"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_116.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Tape Inventorying Job Started


Sent when a user starts a tape inventorying job session. For more information, see [Inventorying Tapes](https://helpcenter.veeam.com/docs/backup/vsphere/inventoring_tapes.html).

General Information

Event ID: 116

Event message details: Tape Inventorying job <JobName> has been started by user <UserName>

Severity: Info

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="6699d585-5290-4589-b2fb-40cc1b70953d" |
| JobID | Job ID. | JobID="3ec9002a-9788-40f4-9a43-b5b690bd4253" |
| JobType | Job type. | JobType="36" |
| Platform | Platform type. | Platform="5" |
| Flags | Defines whether the job was started by a user. | Flags="1" |
| TargetObjectID | Target object ID. | TargetObjectID="00000000-0000-0000-0000-000000000000" |
| TapeIDs | Tape IDs. | TapeIDs="73502813-abc9-4576-849a-903b7d428177" |
| OperationSummary | Operation details. | OperationSummary="Tapes to inventory: HPE007L2" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Tape Inventorying job 'Tape Library Inventorying' has been started by user TECH\user1." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-30T10:58:58.946951+01:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=116 JobSessionID="6699d585-5290-4589-b2fb-40cc1b70953d" JobID="3ec9002a-9788-40f4-9a43-b5b690bd4253" JobType="36" Platform="5" Flags="1" TargetObjectID="00000000-0000-0000-0000-000000000000" TapeIDs="73502813-abc9-4576-849a-903b7d428177" OperationSummary="Tapes to inventory: HPE007L2" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Tape Inventorying job 'Tape Library Inventorying has been started by user TECH\user1."] |


