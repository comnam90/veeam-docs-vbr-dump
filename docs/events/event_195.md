---
title: "Tape Erase Job Finished"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_195.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Tape Erase Job Finished


Sent when a tape erase job session is finished. For more information, see [Erasing Tapes](https://helpcenter.veeam.com/docs/backup/vsphere/erasing_tapes.html).

General Information

Event ID: 195

Event message details: Tape Erase job <JobName> finished with <State>

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="02532b59-4908-44df-9350-bf184faccf5a" |
| JobID | Job ID. | JobID="a66e65ba-a34b-4829-8a62-9c7ad2a91df0" |
| JobResult | Job result ID. Possible values:   * 0 — Success * 1 — Warning * 2 — Failed | JobResult="0" |
| JobType | Job type. | JobType="34" |
| Platform | Platform type. | Platform="5" |
| WillBeRetried | Defines whether the job will be retried. | WillBeRetried="False" |
| JobName | Job name. | JobName="Tape Export" |
| SourceType | Job source type. | SourceType="6" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Tape Erase job 'Tape Export' finished with Success." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-30T11:02:50.798477+01:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=195 JobSessionID="02532b59-4908-44df-9350-bf184faccf5a" JobID="a66e65ba-a34b-4829-8a62-9c7ad2a91df0" JobResult="0" JobType="34" Platform="5" WillBeRetried="False" JobName="Tape Export" SourceType="6" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Tape Erase job 'Tape Export' finished with Success."] |


