---
title: "event_151"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_151.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when a file backup job session is finished. For more information, see [Creating File Backup Jobs](https://helpcenter.veeam.com/docs/backup/vsphere/file_share_backup_job.html).

General Information

Event ID: 151

Event message details: Source <SourceName> task has finished with <State> state. <Details>

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="e2ae09f0-97d5-4e7e-8b5d-51f226f11ce7" |
| JobID | Job ID. | JobID="21d267c3-1746-4806-800b-eca787723eae" |
| JobType | Job type. | JobType="13000" |
| TaskSessionID | Task session ID. | TaskSessionID="8794851b-fbf8-4560-9f59-401d8ca2b921" |
| Status | Session status ID. Possible values:   * 0 — Success * 2 — Failed * 3 — Warning * 5 — In progress * 6 — Pending | Status="0" |
| JobDescription | Job description. | JobDescription="SMB File Share backup" |
| SourceHostName | Source host name. | SourceHostName="\\fs1\Folder" |
| SourceName | Source name. | SourceName="\\fs1\Folder" |
| TransferredGb | Transferred data in GB. | TransferredGb="0.059" |
| Platform | Platform type. | Platform="11" |
| IsRetry | Defines whether the job will be retried. | IsRetry="False" |
| SourceType | Job source type. | SourceType="3" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Source '\\fs1\Folder' task has finished with 'Success' state." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-20T16:11:59.583443+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=151 JobSessionID="e2ae09f0-97d5-4e7e-8b5d-51f226f11ce7" JobID="21d267c3-1746-4806-800b-eca787723eae" JobType="13000" TaskSessionID="8794851b-fbf8-4560-9f59-401d8ca2b921" Status="0" JobDescription="SMB File Share backup" SourceHostName="\\fs1\Folder" SourceName="\\fs1\Folder" TransferredGb="0.059" Platform="11" IsRetry="False" SourceType="3" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Source '\\fs1\Folder' task has finished with 'Success' state."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
