---
title: "event_114"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_114.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when a user starts a file to tape job session. For more information, see [Creating File to Tape Jobs](https://helpcenter.veeam.com/docs/backup/vsphere/creating_file_to_tape_jobs.html).

General Information

Event ID: 114

Event message details: File to Tape Backup job <JobName> has been started by user <UserName>

Severity: Info

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="0132c6cd-da23-448b-ae2d-d99f8a159af4" |
| JobID | Job ID. | JobID="d6438c9f-239c-4728-9dd7-ace7bb36718a" |
| JobType | Job type. | JobType="24" |
| Platform | Platform type. | Platform="5" |
| Flags | Defines whether the job was started by a user. | Flags="1" |
| TargetObjectID | Target object ID. | TargetObjectID="00000000-0000-0000-0000-000000000000" |
| TapeIDs | Tape IDs. | TapeIDs="73502813-abc9-4576-849a-903b7d428177" |
| OperationSummary | Operation details. | OperationSummary="File to tape: HPE007L2" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="File to Tape Backup job 'Files to Tape' has been started by user TECH\user1." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-20T13:28:31.625928+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=114 JobSessionID="0132c6cd-da23-448b-ae2d-d99f8a159af4" JobID="d6438c9f-239c-4728-9dd7-ace7bb36718a" JobType="24" Platform="5" Flags="1" TargetObjectID="00000000-0000-0000-0000-000000000000" TapeIDs="73502813-abc9-4576-849a-903b7d428177" OperationSummary="File to tape: HPE007L2" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="File to Tape Backup job 'Files to Tape' has been started by user TECH\user1."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
