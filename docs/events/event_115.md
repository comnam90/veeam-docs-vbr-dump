---
title: "Tape Erase Job Started"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_115.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Tape Erase Job Started


Sent when a user starts a tape erase job session. For more information, see [Erasing Tapes](https://helpcenter.veeam.com/docs/backup/vsphere/erasing_tapes.html).

General Information

Event ID: 115

Event message details: Tape Erase job <JobName> has been started by user <UserName>

Severity: Info

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="7b5cae3a-6997-400b-afd5-8b789b6489e1" |
| JobID | Job ID. | JobID="6ffc9539-d78c-45cc-9b32-086e140e754a" |
| JobType | Job type. | JobType="32" |
| Platform | Platform type. | Platform="5" |
| Flags | Defines whether the job was started by a user. | Flags="1" |
| TargetObjectID | Target object ID. | TargetObjectID="00000000-0000-0000-0000-000000000000" |
| TapeIDs | Tape IDs. | TapeIDs="73502813-abc9-4576-849a-903b7d428177" |
| OperationSummary | Operation details. | OperationSummary="Tapes to erase: HPE007L2" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Tape Erase job 'Tape Erase' has been started by user TECH\user1." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-30T10:56:46.520387+01:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=115 JobSessionID="7b5cae3a-6997-400b-afd5-8b789b6489e1" JobID="6ffc9539-d78c-45cc-9b32-086e140e754a" JobType="32" Platform="5" Flags="1" TargetObjectID="00000000-0000-0000-0000-000000000000" TapeIDs="73502813-abc9-4576-849a-903b7d428177" OperationSummary="Tapes to erase: HPE007L2" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Tape Erase job 'Tape Erase' has been started by user TECH\user1."] |


