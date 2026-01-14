---
title: "event_120"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_120.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when a user starts a tape copy job session. For more information, see [Copying Tapes](https://helpcenter.veeam.com/docs/backup/vsphere/copying_tapes.html).

General Information

Event ID: 120

Event message details: Tape Copy job <JobName> has been started by user <UserName>

Severity: Info

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="e00b4e4f-0bea-4444-b27c-34f1da944f68" |
| JobID | Job ID. | JobID="1bb59d9d-729e-46a9-944b-4075fe049f79" |
| JobType | Job type. | JobType="501" |
| Platform | Platform type. | Platform="5" |
| Flags | Defines whether the job was started by a user. | Flags="1" |
| TargetMediaPoolID | Target media pool ID. | TargetMediaPoolID="3730b44e-ce27-405b-ac31-d065294746ca" |
| TapeIDs | Tape IDs. | TapeIDs="02fe017d-1e14-4711-85ba-cac8d53c7ec5" |
| OperationSummary | Operation details. | OperationSummary="Tapes to copy: HPE008L2; target pool: HPE - Standard Pool" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Tape Copy job 'Tape Copy' has been started by user TECH\user1." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-30T11:03:42.229899+01:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=120 JobSessionID="e00b4e4f-0bea-4444-b27c-34f1da944f68" JobID="1bb59d9d-729e-46a9-944b-4075fe049f79" JobType="501" Platform="5" Flags="1" TargetMediaPoolID="3730b44e-ce27-405b-ac31-d065294746ca" TapeIDs="02fe017d-1e14-4711-85ba-cac8d53c7ec5" OperationSummary="Tapes to copy: HPE008L2; target pool: HPE - Standard Pool" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Tape Copy job 'Tape Copy' has been started by user TECH\user1."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
