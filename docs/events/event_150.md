---
title: "Backup Task Finished"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_150.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Backup Task Finished


Sent when a backup task is finished. For more information, see [Creating Backup Jobs](https://helpcenter.veeam.com/docs/backup/vsphere/backup_job.html).

General Information

Event ID: 150

Event message details: <VmName> task has finished with <State> state

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="c0d93abe-3adf-4397-b762-351b73acf7e1" |
| JobID | Job ID. | JobID="c4415b30-de82-4403-8816-ea66636356e8" |
| JobType | Job type. | JobType="0" |
| TaskSessionID | Task session ID. | TaskSessionID="5005b373-ad69-4081-a50a-835387c66824" |
| OibID | Machine ID. | OibID="35503d1d-28f9-49ed-82d5-b81c33f9d978" |
| OriginalOibID | Original machine ID. | OriginalOibID="35503d1d-28f9-49ed-82d5-b81c33f9d978" |
| CreationTime | Date and time when a restore point has been created. | CreationTime="03/20/2025 12:34:03" |
| Status | Session status ID. Possible values:   * 0 — Success * 2 — Failed * 3 — Warning * 5 — In progress * 6 — Pending | Status="0" |
| JobDescription | Job description. | JobDescription="Created by Powershell at 03/20/2025 8:56:14 AM." |
| SourceHostName | Source host name. | SourceHostName="pdc01.tech.local" |
| VmRef | Machine reference ID. | VmRef="vm-01" |
| VmName | Machine name. | VmName="VM01" |
| TransferredGb | Transferred data in GB. | TransferredGb="12.731" |
| Platform | Platform type. | Platform="0" |
| IsRetry | Defines whether the job will be retried. | IsRetry="False" |
| SourceType | Job source type. | SourceType="2" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="VM01 task has finished with 'Success' state." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-20T14:36:09.190062+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=150 JobSessionID="c0d93abe-3adf-4397-b762-351b73acf7e1" JobID="c4415b30-de82-4403-8816-ea66636356e8" JobType="0" TaskSessionID="5005b373-ad69-4081-a50a-835387c66824" OibID="35503d1d-28f9-49ed-82d5-b81c33f9d978" OriginalOibID="35503d1d-28f9-49ed-82d5-b81c33f9d978" CreationTime="03/20/2025 12:34:03" Status="0" JobDescription="Created by Powershell at 03/20/2025 8:56:14 AM." SourceHostName="pdc01.tech.local" VmRef="vm-01" VmName="VM01" TransferredGb="12.731" Platform="0" IsRetry="False" SourceType="2" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="VM01 task has finished with 'Success' state."] |


