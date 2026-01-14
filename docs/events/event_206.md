---
title: "event_206"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_206.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when a delete from library job session is finished.

General Information

Event ID: 206

Event message details: Delete from Library job <JobName> finished with <State>

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="dd5e025f-7e6b-467a-94ba-c9e7c2911854" |
| JobID | Job ID. | JobID="61fab03f-3065-431f-a2ef-1e4e141fe8e0" |
| JobResult | Job result ID. Possible values:   * 0 — Success * 1 — Warning * 2 — Failed | JobResult="0" |
| JobType | Job type. | JobType="56" |
| Platform | Platform type. | Platform="5" |
| WillBeRetried | Defines whether the job will be retried. | WillBeRetried="False" |
| JobName | Job name. | JobName="Delete from Library" |
| SourceType | Job source type. | SourceType="6" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Delete from Library job 'Delete from Library' finished with Success." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-30T11:08:29.358624+01:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=206 JobSessionID="dd5e025f-7e6b-467a-94ba-c9e7c2911854" JobID="61fab03f-3065-431f-a2ef-1e4e141fe8e0" JobResult="0" JobType="56" Platform="5" WillBeRetried="False" JobName="Delete from Library" SourceType="6" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Delete from Library job 'Delete from Library' finished with Success."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
