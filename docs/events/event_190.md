---
title: "event_190"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_190.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when a backup job session is finished. For more information, see [Creating Backup Jobs](https://helpcenter.veeam.com/docs/backup/vsphere/backup_job.html).

General Information

Event ID: 190

Event message details: Backup job <JobName> finished with <State>. <Details>

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="c0d93abe-3adf-4397-b762-351b73acf7e1" |
| JobID | Job ID. | JobID="c4415b30-de82-4403-8816-ea66636356e8" |
| JobResult | Job result ID. Possible values:   * 0 — Success * 1 — Warning * 2 — Failed | JobResult="0" |
| JobType | Job type. | JobType="0" |
| Platform | Platform type. | Platform="0" |
| WillBeRetried | Defines whether the job will be retried. | WillBeRetried="False" |
| JobName | Job name. | JobName="VMware Production servers backup" |
| SourceType | Job source type. | SourceType="2" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Backup job 'VMware Production servers backup' finished with Success. All objects have been backed up successfully." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-20T14:36:16.008569+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=190 JobSessionID="c0d93abe-3adf-4397-b762-351b73acf7e1" JobID="c4415b30-de82-4403-8816-ea66636356e8" JobResult="0" JobType="0" Platform="0" WillBeRetried="False" JobName="VMware Production servers backup" SourceType="2" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Backup job 'VMware Production servers backup' finished with Success. All objects have been backed up successfully."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
