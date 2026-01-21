---
title: "Move To Media Pool Job Finished"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_205.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Move To Media Pool Job Finished


Sent when a move to media pool job session is finished. For more information, see [Moving Tapes to Another Media Pool](https://helpcenter.veeam.com/docs/backup/vsphere/moving_tapes_to_custom_pool.html).

General Information

Event ID: 205

Event message details: Move to Media Pool job <JobName> finished with <State>

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="7f1ffcb6-698a-4c42-b8b2-c2f518a5d620" |
| JobID | Job ID. | JobID="bc6e8331-8781-4fc7-85ec-9dd5c7687f3a" |
| JobResult | Job result ID. Possible values:   * 0 — Success * 1 — Warning * 2 — Failed | JobResult="0" |
| JobType | Job type. | JobType="57" |
| Platform | Platform type. | Platform="5" |
| WillBeRetried | Defines whether the job will be retried. | WillBeRetried="False" |
| JobName | Job name. | JobName="Move to Media Pool" |
| SourceType | Job source type. | SourceType="6" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Move to Media Pool job 'Move to Media Pool' finished with Success." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-30T11:08:20.803462+01:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=205 JobSessionID="7f1ffcb6-698a-4c42-b8b2-c2f518a5d620" JobID="bc6e8331-8781-4fc7-85ec-9dd5c7687f3a" JobResult="0" JobType="57" Platform="5" WillBeRetried="False" JobName="Move to Media Pool" SourceType="6" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Move to Media Pool job 'Move to Media Pool' finished with Success."] |


