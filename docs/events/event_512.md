---
title: "event_512"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_512.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when a user starts a VM copy job session. For more information, see [VM Copy](https://helpcenter.veeam.com/docs/backup/vsphere/vm_copy.html).

General Information

Event ID: 512

Event message details: Copy job <JobName> has been started by user <UserName>

Severity: Info

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="a827df34-d63b-4536-b2f7-f0cf451109cb" |
| JobID | Job ID. | JobID="42686b4c-1e75-4d24-b64b-47923e2de189" |
| JobType | Job type. | JobType="2" |
| Platform | Platform type. | Platform="0" |
| Flags | Defines whether the job was started by a user. | Flags="0" |
| SourceType | Job source type. | SourceType="2" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Copy job 'VM Copy Job 02' has been started by user TECH\user1." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-20T19:11:26.068734+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=512 JobSessionID="a827df34-d63b-4536-b2f7-f0cf451109cb" JobID="42686b4c-1e75-4d24-b64b-47923e2de189" JobType="2" Platform="0" Flags="0" SourceType="2" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Copy job 'VM Copy Job 02' has been started by user TECH\user1."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
