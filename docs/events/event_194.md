---
title: "File to Tape Job Finished"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_194.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# File to Tape Job Finished


Sent when a file to tape job session is finished. For more information, see [Creating File to Tape Jobs](https://helpcenter.veeam.com/docs/backup/vsphere/creating_file_to_tape_jobs.html).

General Information

Event ID: 194

Event message details: File to Tape Backup job <JobName> finished with <State>

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="0132c6cd-da23-448b-ae2d-d99f8a159af4" |
| JobID | Job ID. | JobID="d6438c9f-239c-4728-9dd7-ace7bb36718a" |
| JobResult | Job result ID. Possible values:   * 0 — Success * 1 — Warning * 2 — Failed | JobResult="0" |
| JobType | Job type. | JobType="24" |
| Platform | Platform type. | Platform="5" |
| WillBeRetried | Defines whether the job will be retried. | WillBeRetried="False" |
| JobName | Job name. | JobName="Files to Tape" |
| SourceType | Job source type. | SourceType="3" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="File to Tape Backup job 'Files to Tape' finished with Success." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-20T13:28:43.744565+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=194 JobSessionID="0132c6cd-da23-448b-ae2d-d99f8a159af4" JobID="d6438c9f-239c-4728-9dd7-ace7bb36718a" JobResult="0" JobType="24" Platform="5" WillBeRetried="False" JobName="Files to Tape" SourceType="3" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="File to Tape Backup job 'Files to Tape' finished with Success."] |


