---
title: "VM Copy Job Finished"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_592.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# VM Copy Job Finished


Sent when a VM copy job session is finished. For more information, see [VM Copy](https://helpcenter.veeam.com/docs/backup/vsphere/vm_copy.html).

General Information

Event ID: 592

Event message details: Copy job <JobName> finished with <State>

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="a827df34-d63b-4536-b2f7-f0cf451109cb" |
| JobID | Job ID. | JobID="42686b4c-1e75-4d24-b64b-47923e2de189" |
| JobResult | Job result ID. Possible values:   * 0 — Success * 1 — Warning * 2 — Failed | JobResult="0" |
| JobType | Job type. | JobType="2" |
| Platform | Platform type. | Platform="0" |
| WillBeRetried | Defines whether the job will be retried. | WillBeRetried="False" |
| JobName | Job name. | JobName="VM Copy Job 02" |
| SourceType | Job source type. | SourceType="2" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Copy job 'VM Copy Job 02' finished with Success." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-20T19:12:07.328602+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=592 JobSessionID="a827df34-d63b-4536-b2f7-f0cf451109cb" JobID="42686b4c-1e75-4d24-b64b-47923e2de189" JobResult="0" JobType="2" Platform="0" WillBeRetried="False" JobName="VM Copy Job 02" SourceType="2" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Copy job 'VM Copy Job 02' finished with Success."] |


