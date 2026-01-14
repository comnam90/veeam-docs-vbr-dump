---
title: "event_650"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_650.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when a user starts an active full backup for the backup policy. For more information, see [Performing Active Full Backup](https://helpcenter.veeam.com/docs/backup/agents/agent_policy_active_full.html).

General Information

Event ID: 650

Event message details: Agent Active Full for <JobName> has been started by user <UserName>

Severity: Info

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="9cbb9163-6791-4d7d-a6a9-744210d7e6a6" |
| JobID | Job ID. | JobID="7eb18610-9aca-4cb5-9b37-8d7051887911" |
| JobType | Job type. | JobType="12008" |
| Platform | Platform type. | Platform="6" |
| Flags | Defines whether the job was started by a user. | Flags="1" |
| SourceType | Job source type. | SourceType="5" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Agent Active Full for 'Agent Backup Policy 1' has been started by user TECH\user1." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-23T16:18:29.774023+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=650 JobSessionID="9cbb9163-6791-4d7d-a6a9-744210d7e6a6" JobID="7eb18610-9aca-4cb5-9b37-8d7051887911" JobType="12008" Platform="6" Flags="1" SourceType="5" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Agent Active Full for 'Agent Backup Policy 1' has been started by user TECH\user1."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
