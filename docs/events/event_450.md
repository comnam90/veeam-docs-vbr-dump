---
title: "event_450"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_450.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when a backup copy task is finished. For more information, see [Backup Copy](https://helpcenter.veeam.com/docs/backup/vsphere/backup_copy.html).

General Information

Event ID: 450

Event message details: <VmName> task has finished with <State> state

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="2053dad3-63d6-4990-88bd-66fa4e2ef28d" |
| JobID | Job ID. | JobID="f03100a2-4d32-4ddc-a0d0-85759083e2de" |
| JobType | Job type. | JobType="63" |
| TaskSessionID | Task session ID. | TaskSessionID="48f7ab45-c494-4147-8af3-bcb7fef16a0c" |
| OibID | Machine ID. | OibID="3d3ddf15-7a18-491d-a2b7-087c99ab6395" |
| OriginalOibID | Original machine ID. | OriginalOibID="14db33a5-cec2-44e6-b3a2-f355ca2f542f" |
| CreationTime | Date and time when a restore point has been created. | CreationTime="03/24/2025 06:54:02" |
| Status | Session status ID. Possible values:   * 0 — Success * 2 — Failed * 3 — Warning * 5 — In progress * 6 — Pending | Status="5" |
| JobDescription | Job description. | JobDescription="VM01 backup copy task" |
| SourceHostName | Source host name. | SourceHostName="pdc01.tech.local" |
| VmRef | Machine reference ID. | VmRef="vm-01" |
| VmName | Machine name. | VmName="VM01" |
| TransferredGb | Transferred data in GB. | TransferredGb="0.011" |
| Platform | Platform type. | Platform="0" |
| IsRetry | Defines whether the job will be retried. | IsRetry="False" |
| SourceType | Job source type. | SourceType="2" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="VM01 task has finished with 'InProgress' state." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-24T13:06:25.751766+02:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=450 JobSessionID="2053dad3-63d6-4990-88bd-66fa4e2ef28d" JobID="f03100a2-4d32-4ddc-a0d0-85759083e2de" JobType="63" TaskSessionID="48f7ab45-c494-4147-8af3-bcb7fef16a0c" OibID="3d3ddf15-7a18-491d-a2b7-087c99ab6395" OriginalOibID="14db33a5-cec2-44e6-b3a2-f355ca2f542f" CreationTime="03/24/2025 06:54:02" Status="5" JobDescription="VM01 backup copy task" SourceHostName="pdc01.tech.local" VmRef="vm-01" VmName="VM01" TransferredGb="0.011" Platform="0" IsRetry="False" SourceType="2" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="VM01 task has finished with 'InProgress' state."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
