---
title: "event_410"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_410.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when a user starts a backup copy job session. For more information, see [Backup Copy](https://helpcenter.veeam.com/docs/backup/vsphere/backup_copy.html).

General Information

Event ID: 410

Event message details: Backup Copy job <JobName> has been started

Severity: Info

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="11ce771c-54f1-444a-ae1a-ee76c96eabe9" |
| JobID | Job ID. | JobID="c4adcbc0-ef2f-4a12-8cc4-0f07fb3df2fa" |
| JobType | Job type. | JobType="13003" |
| Platform | Platform type. | Platform="11" |
| Flags | Defines whether the job was started by a user. | Flags="0" |
| SourceType | Job source type. | SourceType="3" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Backup Copy job 'Fileshare SMB backup (Copy) 1' has been started." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-20T16:11:25.904092+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=410 JobSessionID="11ce771c-54f1-444a-ae1a-ee76c96eabe9" JobID="c4adcbc0-ef2f-4a12-8cc4-0f07fb3df2fa" JobType="13003" Platform="11" Flags="0" SourceType="3" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Backup Copy job 'Fileshare SMB backup (Copy) 1' has been started."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
