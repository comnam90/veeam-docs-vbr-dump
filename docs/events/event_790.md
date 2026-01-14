---
title: "event_790"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_790.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when an agent backup job session is finished. For more information, see [Starting and Stopping Veeam Agent Backup Job](https://helpcenter.veeam.com/docs/backup/agents/agent_job_start_stop.html).

General Information

Event ID: 790

Event message details: Agent Backup job <JobName> finished with <State>. <Details>

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="3334a4f4-54b6-4d0c-8045-cdc329817693" |
| JobID | Job ID. | JobID="3f427354-5bc1-492a-ae5b-f307bf1a9ab3" |
| JobResult | Job result ID. Possible values:   * 0 — Success * 1 — Warning * 2 — Failed | JobResult="0" |
| JobType | Job type. | JobType="12003" |
| Platform | Platform type. | Platform="6" |
| WillBeRetried | Defines whether the job will be retried. | WillBeRetried="False" |
| JobName | Job name. | JobName="Agent Backup Job 1" |
| SourceType | Job source type. | SourceType="5" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Agent Backup job 'Agent Backup Job 1' finished with Success. All objects have been backed up successfully." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-23T16:08:19.229942+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=790 JobSessionID="3334a4f4-54b6-4d0c-8045-cdc329817693" JobID="3f427354-5bc1-492a-ae5b-f307bf1a9ab3" JobResult="0" JobType="12003" Platform="6" WillBeRetried="False" JobName="Agent Backup Job 1" SourceType="5" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Agent Backup job 'Agent Backup Job 1' finished with Success. All objects have been backed up successfully."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
