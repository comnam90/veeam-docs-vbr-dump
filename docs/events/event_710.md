---
title: "event_710"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_710.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when a user starts an agent backup job session. For more information, see [Starting and Stopping Veeam Agent Backup Job](https://helpcenter.veeam.com/docs/backup/agents/agent_job_start_stop.html).

General Information

Event ID: 710

Event message details: Agent Backup job <JobName> has been started by user <UserName>

Severity: Info

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="3334a4f4-54b6-4d0c-8045-cdc329817693" |
| JobID | Job ID. | JobID="3f427354-5bc1-492a-ae5b-f307bf1a9ab3" |
| JobType | Job type. | JobType="12003" |
| Platform | Platform type. | Platform="6" |
| Flags | Defines whether the job was started by a user. | Flags="1" |
| SourceType | Job source type. | SourceType="5" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Agent Backup job 'Agent Backup Job 1' has been started by TECH\user1." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-23T15:59:47.415672+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=710 JobSessionID="3334a4f4-54b6-4d0c-8045-cdc329817693" JobID="3f427354-5bc1-492a-ae5b-f307bf1a9ab3" JobType="12003" Platform="6" Flags="1" SourceType="5" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Agent Backup job 'Agent Backup Job 1' has been started by TECH\user1."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
