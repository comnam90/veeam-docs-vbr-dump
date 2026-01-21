---
title: "SureBackup Job Finished"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_390.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# SureBackup Job Finished


Sent when a SureBackup job session is finished. For more information, see [SureBackup Job](https://helpcenter.veeam.com/docs/backup/vsphere/surebackup_job.html).

General Information

Event ID: 390

Event message details: SureBackup job <JobName> finished with <State>. <Details>

Severity: Info, Waring, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="5d899b75-448e-4a1a-a0b7-851f06e818fd" |
| JobID | Job ID. | JobID="edc5270e-9cc4-4700-aff2-eff08302315c" |
| JobResult | Job result ID. Possible values:   * 0 — Success * 1 — Warning * 2 — Failed | JobResult="2" |
| JobType | Job type. | JobType="3" |
| Platform | Platform type. | Platform="1" |
| WillBeRetried | Defines whether the job will be retried. | WillBeRetried="False" |
| JobName | Job name. | JobName="SureBackup Job 1" |
| SourceType | Job source type. | SourceType="5" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="SureBackup job 'SureBackup Job 1' finished with Failed. Job details: Failed to connect to proxy appliance VM using IPv4 address." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-20T13:35:32.709942+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=390 JobSessionID="5d899b75-448e-4a1a-a0b7-851f06e818fd" JobID="edc5270e-9cc4-4700-aff2-eff08302315c" JobResult="2" JobType="3" Platform="1" WillBeRetried="False" JobName="SureBackup Job 1" SourceType="5" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="SureBackup job 'SureBackup Job 1' finished with Failed. Job details: Failed to connect to proxy appliance VM using IPv4 address."] |


