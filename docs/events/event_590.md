---
title: "File Copy Job Finished"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_590.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# File Copy Job Finished


Sent when a file copy job session is finished. For more information, see [File Copy](https://helpcenter.veeam.com/docs/backup/vsphere/file_copy.html).

General Information

Event ID: 590

Event message details: Copy job <JobName> finished with <State>

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="5e1e878a-cfe2-4bb0-bca4-cee33c468162" |
| JobID | Job ID. | JobID="226e0318-0bb9-4d22-bf1a-f4c0fa51eb1d" |
| JobResult | Job result ID. Possible values:   * 0 — Success * 1 — Warning * 2 — Failed | JobResult="0" |
| JobType | Job type. | JobType="2" |
| Platform | Platform type. | Platform="0" |
| WillBeRetried | Defines whether the job will be retried. | WillBeRetried="False" |
| JobName | Job name. | JobName="File Copy Job 02" |
| SourceType | Job source type. | SourceType="3" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Copy job 'File Copy Job 02' finished with Success." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-20T19:10:23.353785+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=590 JobSessionID="5e1e878a-cfe2-4bb0-bca4-cee33c468162" JobID="226e0318-0bb9-4d22-bf1a-f4c0fa51eb1d" JobResult="0" JobType="2" Platform="0" WillBeRetried="False" JobName="File Copy Job 02" SourceType="3" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Copy job 'File Copy Job 02' finished with Success."] |


