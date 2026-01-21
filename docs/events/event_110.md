---
title: "Backup Job Started"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_110.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Backup Job Started


Sent when a user starts a backup job session. For more information, see [Creating Backup Jobs](https://helpcenter.veeam.com/docs/backup/vsphere/backup_job.html).

General Information

Event ID: 110

Event message details: Backup job <JobName> has been started by user <UserName>

Severity: Info

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="c0d93abe-3adf-4397-b762-351b73acf7e1" |
| JobID | Job ID. | JobID="c4415b30-de82-4403-8816-ea66636356e8" |
| JobType | Job type. | JobType="0" |
| Platform | Platform type. | Platform="0" |
| Flags | Defines whether the job was started by a user. | Flags="1" |
| SourceType | Job source type. | SourceType="2" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="Backup job 'VMware Production servers backup' has been started by user TECH\user1." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-20T14:32:51.289460+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=110 JobSessionID="c0d93abe-3adf-4397-b762-351b73acf7e1" JobID="c4415b30-de82-4403-8816-ea66636356e8" JobType="0" Platform="0" Flags="1" SourceType="2" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="Backup job 'VMware Production servers backup' has been started by user TECH\user1."] |


