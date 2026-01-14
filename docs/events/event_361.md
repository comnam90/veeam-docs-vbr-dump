---
title: "event_361"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_361.html"
last_updated: "12/5/2025"
product_version: "13.0.1.180"
---


In this article

Sent when a validation task for a Hyper-V VM is finished. For more information, see [SureBackup Job](https://helpcenter.veeam.com/docs/backup/vsphere/surebackup_job.html).

General Information

Event ID: 361

Event message details: VM <VmName> validation task has finished with <State> state

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="da83c52f-a52b-41f6-a524-39d3d743e7b6" |
| JobID | Job ID. | JobID="cc7a04c3-2215-4be0-a96c-f0c059ddffe3" |
| JobType | Job type. | JobType="3" |
| TaskSessionID | Task session ID. | TaskSessionID="f1e40437-5e16-4baf-9621-da980df22d9e" |
| TaskSessionType | Task session type. | TaskSessionType="1" |
| Result | Session result ID. Possible values:   * 0 — Success * 1 — Warning * 2 — Failed | Result="0" |
| OibID | Machine ID. | OibID="3f36cedd-42e8-4362-87d1-5670b754673a" |
| IsSureReplica | Defines whether the task is SureReplica. | IsSureReplica="False" |
| HostName | Host name. | HostName="hvsrv01.tech.local" |
| VmLocation | Machine location. | VmLocation="C:\ClusterStorage\Volume1\VMs\VM01" |
| VmName | Machine name. | VmName="VM01" |
| VmID | Machine ID. | VmID="2c508117-f5aa-44dc-889f-6476b406f777" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="VM [VM01] validation task has finished with [Success] state." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-24T03:39:04.043853-07:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=361 JobSessionID="da83c52f-a52b-41f6-a524-39d3d743e7b6" JobID="cc7a04c3-2215-4be0-a96c-f0c059ddffe3" JobType="3" TaskSessionID="f1e40437-5e16-4baf-9621-da980df22d9e" TaskSessionType="1" Result="1" OibID="3f36cedd-42e8-4362-87d1-5670b754673a" IsSureReplica="False" HostName="hvsrv01.tech.local" VmLocation="C:\ClusterStorage\Volume1\VMs\VM01" VmName="VM01" VmID="2c508117-f5aa-44dc-889f-6476b406f777" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="VM [VM01] validation task has finished with [Success] state."] |

Page updated 12/5/2025

Page content applies to build 13.0.1.180
