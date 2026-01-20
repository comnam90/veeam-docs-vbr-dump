---
title: "Mark Tape As Free Job Finished"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_204.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Mark Tape As Free Job Finished


Sent when a mark tape as free job session is finished. For more information, see [Marking Tapes as Free](https://helpcenter.veeam.com/docs/backup/vsphere/marking_tapes_as_free.html).

General Information

Event ID: 204

Event message details: Mark as Free job <JobName> finished with <State>

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="e905fe5d-72fb-4d1c-beff-b9eee2f9861b" |
| JobID | Job ID. | JobID="af8071ed-2ce4-4cdd-93a5-244c18364c48" |
| JobResult | Job result ID. Possible values:   * 0 — Success * 1 — Warning * 2 — Failed | JobResult="0" |
| JobType | Job type. | JobType="55" |
| Platform | Platform type. | Platform="5" |
| WillBeRetried | Defines whether the job will be retried. | WillBeRetried="False" |
| JobName | Job name. | JobName="Mark as Free" |
| SourceType | Job source type. | SourceType="6" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Mark as Free job 'Mark as Free' finished with Success." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-30T11:08:11.656473+01:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=204 JobSessionID="e905fe5d-72fb-4d1c-beff-b9eee2f9861b" JobID="af8071ed-2ce4-4cdd-93a5-244c18364c48" JobResult="0" JobType="55" Platform="5" WillBeRetried="False" JobName="Mark as Free" SourceType="6" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Mark as Free job 'Mark as Free' finished with Success."] |


