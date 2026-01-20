---
title: "File Copy Job Started"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_510.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# File Copy Job Started


Sent when a user starts a file copy job session. For more information, see [File Copy](https://helpcenter.veeam.com/docs/backup/vsphere/file_copy.html).

General Information

Event ID: 510

Event message details: Copy job <JobName> has been started by user <UserName>

Severity: Info

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="5e1e878a-cfe2-4bb0-bca4-cee33c468162" |
| JobID | Job ID. | JobID="226e0318-0bb9-4d22-bf1a-f4c0fa51eb1d" |
| JobType | Job type. | JobType="2" |
| Platform | Platform type. | Platform="0" |
| Flags | Defines whether the job was started by a user. | Flags="0" |
| SourceType | Job source type. | SourceType="3" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Copy job 'File Copy Job 02' has been started by user TECH\user1." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-20T19:10:13.252692+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=510 JobSessionID="5e1e878a-cfe2-4bb0-bca4-cee33c468162" JobID="226e0318-0bb9-4d22-bf1a-f4c0fa51eb1d" JobType="2" Platform="0" Flags="0" SourceType="3" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Copy job 'File Copy Job 02' has been started by user TECH\user1."] |


