---
title: "File Backup Copy Job Finished"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_451.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# File Backup Copy Job Finished


Sent when a file backup copy job session is finished. For more information, see [Creating File Backup Jobs](https://helpcenter.veeam.com/docs/backup/vsphere/file_share_backup_job.html).

General Information

Event ID: 451

Event message details: Source <SourceName> task has finished with <State> state. <Details>

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="befc9479-9fcf-4e6f-99c3-15f7c2eb51f1" |
| JobID | Job ID. | JobID="c4adcbc0-ef2f-4a12-8cc4-0f07fb3df2fa" |
| JobType | Job type. | JobType="13003" |
| TaskSessionID | Task session ID. | TaskSessionID="fad74fa0-d018-4569-a735-34f3ab5041d6" |
| Status | Session status ID. Possible values:   * 0 — Success * 2 — Failed * 3 — Warning * 5 — In progress * 6 — Pending | Status="2" |
| JobDescription | Job description. | JobDescription="Created by TECH\user1 at 03/20/2025 12:35:07 PM." |
| SourceHostName | Source host name. | SourceHostName="\\fs1\Folder" |
| SourceName | Source name. | SourceName="\\fs1\Folder" |
| TransferredGb | Transferred data in GB. | TransferredGb="0.000" |
| Platform | Platform type. | Platform="11" |
| IsRetry | Defines whether the job will be retried. | IsRetry="False" |
| SourceType | Job source type. | SourceType="3" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Source '\\fs1\Folder' task has finished with 'Failed' state. Task details: Copying restore point 03/20/2025 4:11:31 PM (20 GB): 1 files (0 B) transferred at 0 KB/s. Connection was lost, task will be cancelled." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-20T16:16:51.069076+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=451 JobSessionID="befc9479-9fcf-4e6f-99c3-15f7c2eb51f1" JobID="c4adcbc0-ef2f-4a12-8cc4-0f07fb3df2fa" JobType="13003" TaskSessionID="fad74fa0-d018-4569-a735-34f3ab5041d6" Status="2" JobDescription="Created by TECH\user1 at 03/20/2025 12:35:07 PM." SourceHostName="\\fs1\Folder" SourceName="\\fs1\Folder" TransferredGb="0.000" Platform="11" IsRetry="False" SourceType="3" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Source '\\fs1\Folder' task has finished with 'Failed' state. Task details: Copying restore point 03/20/2025 4:11:31 PM (20 GB): 1 files (0 B) transferred at 0 KB/s. Connection was lost, task will be cancelled."] |


