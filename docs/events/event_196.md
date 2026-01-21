---
title: "Tape Inventorying Job Finished"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_196.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Tape Inventorying Job Finished


Sent when a tape inventorying job session is finished. For more information, see [Inventorying Tapes](https://helpcenter.veeam.com/docs/backup/vsphere/inventoring_tapes.html).

General Information

Event ID: 196

Event message details: Tape Inventorying job <JobName> finished with <State>

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="6699d585-5290-4589-b2fb-40cc1b70953d" |
| JobID | Job ID. | JobID="3ec9002a-9788-40f4-9a43-b5b690bd4253" |
| JobResult | Job result ID. Possible values:   * 0 — Success * 1 — Warning * 2 — Failed | JobResult="0" |
| JobType | Job type. | JobType="36" |
| Platform | Platform type. | Platform="5" |
| WillBeRetried | Defines whether the job will be retried. | WillBeRetried="False" |
| JobName | Job name. | JobName="Tape Library Inventorying" |
| SourceType | Job source type. | SourceType="6" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Tape Inventorying job 'Tape Library Inventorying' finished with Success." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-30T10:59:03.730613+01:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=196 JobSessionID="6699d585-5290-4589-b2fb-40cc1b70953d" JobID="3ec9002a-9788-40f4-9a43-b5b690bd4253" JobResult="0" JobType="36" Platform="5" WillBeRetried="False" JobName="Tape Library Inventorying" SourceType="6" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Tape Inventorying job 'Tape Library Inventorying' finished with Success."] |


