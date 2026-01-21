---
title: "Library Discovery Job Finished"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_207.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Library Discovery Job Finished


Sent when a library discovery job session is finished. For more information, see [Inventorying Tapes](https://helpcenter.veeam.com/docs/backup/vsphere/inventoring_tapes.html).

General Information

Event ID: 207

Event message details: Tape Library Discovery job <JobName> finished with <State>

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="e0688fcb-f2e6-4cff-88d3-2bc5b5bb52ac" |
| JobID | Job ID. | JobID="c20a44f0-30a5-425b-96d5-ab6ffbc41bad" |
| JobResult | Job result ID. Possible values:   * 0 — Success * 1 — Warning * 2 — Failed | JobResult="0" |
| JobType | Job type. | JobType="37" |
| Platform | Platform type. | Platform="5" |
| WillBeRetried | Defines whether the job will be retried. | WillBeRetried="False" |
| JobName | Job name. | JobName="Tape Library Discovery" |
| SourceType | Job source type. | SourceType="6" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Tape Library Discovery job 'Tape Library Discovery' finished with Success." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-30T11:15:58.243835+01:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=207 JobSessionID="e0688fcb-f2e6-4cff-88d3-2bc5b5bb52ac" JobID="c20a44f0-30a5-425b-96d5-ab6ffbc41bad" JobResult="0" JobType="37" Platform="5" WillBeRetried="False" JobName="Tape Library Discovery" SourceType="6" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Tape Library Discovery job 'Tape Library Discovery' finished with Success."] |


