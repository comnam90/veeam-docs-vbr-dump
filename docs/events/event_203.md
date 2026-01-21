---
title: "Tape Eject Job Finished"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_203.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Tape Eject Job Finished


Sent when a tape eject job session is finished. For more information, see [Ejecting Tapes](https://helpcenter.veeam.com/docs/backup/vsphere/ejecting_tapes.html).

General Information

Event ID: 203

Event message details: Tape Eject job <JobName> finished with <State>

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="d87d298a-c4e2-428d-8493-7b535975715d" |
| JobID | Job ID. | JobID="3257e163-8a43-4426-a6f4-cf3acb5345e9" |
| JobResult | Job result ID. Possible values:   * 0 — Success * 1 — Warning * 2 — Failed | JobResult="0" |
| JobType | Job type. | JobType="33" |
| Platform | Platform type. | Platform="5" |
| WillBeRetried | Defines whether the job will be retried. | WillBeRetried="False" |
| JobName | Job name. | JobName="Tape Eject" |
| SourceType | Job source type. | SourceType="6" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Tape Eject job 'Tape Eject' finished with Success." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-30T11:03:09.390196+01:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=203 JobSessionID="d87d298a-c4e2-428d-8493-7b535975715d" JobID="3257e163-8a43-4426-a6f4-cf3acb5345e9" JobResult="0" JobType="33" Platform="5" WillBeRetried="False" JobName="Tape Eject" SourceType="6" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Tape Eject job 'Tape Eject' finished with Success."] |


