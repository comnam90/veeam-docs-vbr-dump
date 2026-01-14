---
title: "event_310"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_310.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when a user starts a SureBackup job session. For more information, see [SureBackup Job](https://helpcenter.veeam.com/docs/backup/vsphere/surebackup_job.html).

General Information

Event ID: 310

Event message details: SureBackup job <JobName> has been started by user <UserName>

Severity: Info

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="5d899b75-448e-4a1a-a0b7-851f06e818fd" |
| JobID | Job ID. | JobID="edc5270e-9cc4-4700-aff2-eff08302315c" |
| JobType | Job type. | JobType="3" |
| Platform | Platform type. | Platform="1" |
| Flags | Defines whether the job was started by a user. | Flags="1" |
| SourceType | Job source type. | SourceType="5" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="SureBackup job 'SureBackup Job 1' has been started by user TECH\user1." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-20T13:31:32.217805+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=310 JobSessionID="5d899b75-448e-4a1a-a0b7-851f06e818fd" JobID="edc5270e-9cc4-4700-aff2-eff08302315c" JobType="3" Platform="1" Flags="1" SourceType="5" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="SureBackup job 'SureBackup Job 1' has been started by user TECH\user1."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
