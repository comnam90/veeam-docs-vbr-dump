---
title: "event_652"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_652.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when an active full backup for the backup policy is finished. r more information, see [Performing Active Full Backup](https://helpcenter.veeam.com/docs/backup/agents/agent_policy_active_full.html).

General Information

Event ID: 652

Event message details: Agent Active Full for <JobName> has finished with <State>

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="9cbb9163-6791-4d7d-a6a9-744210d7e6a6" |
| JobID | Job ID. | JobID="7eb18610-9aca-4cb5-9b37-8d7051887911" |
| JobResult | Job result ID. Possible values:   * 0 — Success * 1 — Warning * 2 — Failed | JobResult="0" |
| JobType | Job type. | JobType="12008" |
| Platform | Platform type. | Platform="6" |
| WillBeRetried | Defines whether the job will be retried. | WillBeRetried="False" |
| JobName | Job name. | JobName="Agent Backup Policy 1" |
| SourceType | Job source type. | SourceType="5" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Agent Active Full for 'Agent Backup Policy 1' has finished with Success." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-23T16:20:45.269895+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=652 JobSessionID="9cbb9163-6791-4d7d-a6a9-744210d7e6a6" JobID="7eb18610-9aca-4cb5-9b37-8d7051887911" JobResult="0" JobType="12008" Platform="6" WillBeRetried="False" JobName="Agent Backup Policy 1" SourceType="5" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Agent Active Full for 'Agent Backup Policy 1' has finished with Success."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
