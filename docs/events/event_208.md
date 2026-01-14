---
title: "event_208"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_208.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when a tape import job session is finished. For more information, see [Loading Tapes](https://helpcenter.veeam.com/docs/backup/vsphere/import_tapes.html).

General Information

Event ID: 208

Event message details: Tape Import job <JobName> finished with <State>

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="8f26e24f-eeac-4606-9502-cf2ff0152af6" |
| JobID | Job ID. | JobID="5137cdc1-9bc4-44e3-994c-919b4b709451" |
| JobResult | Job result ID. Possible values:   * 0 — Success * 1 — Warning * 2 — Failed | JobResult="1" |
| JobType | Job type. | JobType="35" |
| Platform | Platform type. | Platform="5" |
| WillBeRetried | Defines whether the job will be retried. | WillBeRetried="False" |
| JobName | Job name. | JobName="Tape Import" |
| SourceType | Job source type. | SourceType="6" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Tape Import job 'Tape Import' finished with Warning. Job details: No tapes for import found in I/E ports. Completed with warning at Monday, March 31, 2025 10:59:26 AM" |

Syslog Message Example

|  |
| --- |
| 1 2025-11-31T10:59:26.418165+01:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=208 JobSessionID="8f26e24f-eeac-4606-9502-cf2ff0152af6" JobID="5137cdc1-9bc4-44e3-994c-919b4b709451" JobResult="1" JobType="35" Platform="5" WillBeRetried="False" JobName="Tape Import" SourceType="6" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Tape Import job 'Tape Import' finished with Warning. Job details: No tapes for import found in I/E ports. Completed with warning at Monday, March 31, 2025 10:59:26 AM"] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
