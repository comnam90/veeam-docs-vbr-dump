---
title: "event_200"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_200.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when a tape copy job session is finished. For more information, see [Copying Tapes](https://helpcenter.veeam.com/docs/backup/vsphere/copying_tapes.html).

General Information

Event ID: 200

Event message details: Tape Copy job <JobName> finished with <State>

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="e00b4e4f-0bea-4444-b27c-34f1da944f68" |
| JobID | Job ID. | JobID="1bb59d9d-729e-46a9-944b-4075fe049f79" |
| JobResult | Job result ID. Possible values:   * 0 — Success * 1 — Warning * 2 — Failed | JobResult="0" |
| JobType | Job type. | JobType="501" |
| Platform | Platform type. | Platform="5" |
| WillBeRetried | Defines whether the job will be retried. | WillBeRetried="False" |
| JobName | Job name. | JobName="Tape Copy" |
| SourceType | Job source type. | SourceType="6" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Tape Copy job 'Tape Copy' finished with Success." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-30T11:04:11.064253+01:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=200 JobSessionID="e00b4e4f-0bea-4444-b27c-34f1da944f68" JobID="1bb59d9d-729e-46a9-944b-4075fe049f79" JobResult="0" JobType="501" Platform="5" WillBeRetried="False" JobName="Tape Copy" SourceType="6" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Tape Copy job 'Tape Copy' finished with Success."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
