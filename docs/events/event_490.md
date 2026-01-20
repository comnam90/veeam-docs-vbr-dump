---
title: "Backup Copy Job Finished"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_490.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Backup Copy Job Finished


Sent when a backup copy job session is finished. For more information, see [Backup Copy](https://helpcenter.veeam.com/docs/backup/vsphere/backup_copy.html).

General Information

Event ID: 490

Event message details: Backup Copy job <JobName> finished with <State>. <Details>

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="11ce771c-54f1-444a-ae1a-ee76c96eabe9" |
| JobID | Job ID. | JobID="c4adcbc0-ef2f-4a12-8cc4-0f07fb3df2fa" |
| JobResult | Job result ID. Possible values:   * 0 — Success * 1 — Warning * 2 — Failed | JobResult="0" |
| JobType | Job type. | JobType="13003" |
| Platform | Platform type. | Platform="11" |
| WillBeRetried | Defines whether the job will be retried. | WillBeRetried="False" |
| JobName | Job name. | JobName="Fileshare SMB backup (Copy) 1" |
| SourceType | Job source type. | SourceType="3" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Backup Copy job 'Fileshare SMB backup (Copy) 1' finished with Success. All objects have been backed up successfully." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-20T16:11:38.164505+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=490 JobSessionID="11ce771c-54f1-444a-ae1a-ee76c96eabe9" JobID="c4adcbc0-ef2f-4a12-8cc4-0f07fb3df2fa" JobResult="0" JobType="13003" Platform="11" WillBeRetried="False" JobName="Fileshare SMB backup (Copy) 1" SourceType="3" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Backup Copy job 'Fileshare SMB backup (Copy) 1' finished with Success. All objects have been backed up successfully."] |


