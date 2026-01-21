---
title: "Validation Task for VMware VM Finished"
product: "vbr"
doc_type: "events"
source_url: "https://helpcenter.veeam.com/docs/vbr/events/event_351.html"
last_updated: "12/5/2025"
product_version: "13.0.1.1071"
---

# Validation Task for VMware VM Finished


Sent when a validation task for a VMware VM is finished. For more information, see [SureBackup Job](https://helpcenter.veeam.com/docs/backup/vsphere/surebackup_job.html).

General Information

Event ID: 351

Event message details: VM <VmName> validation task has finished with <State> state

Severity: Info, Warning, Error

Parameters

| Parameter Name | Description | Example |
| --- | --- | --- |
| JobSessionID | Job session ID. | JobSessionID="4467f18a-d9e1-4fcf-ae1d-f635eb26cbe9" |
| JobID | Job ID. | JobID="21874156-34b0-4316-94ae-fb05b2f67ec4" |
| JobType | Job type. | JobType="3" |
| TaskSessionID | Task session ID. | TaskSessionID="4cf4d768-18f6-4189-afa1-6f5375dd561c" |
| TaskSessionType | Task session type. | TaskSessionType="1" |
| Result | Session result ID. Possible values:   * 0 — Success * 1 — Warning * 2 — Failed | Result="2" |
| OibID | Machine ID. | OibID="d844fe29-818d-4da6-8adb-f9b6759d241a" |
| IsSureReplica | Defines whether the task is SureReplica. | IsSureReplica="False" |
| HostName | Host name. | HostName="srv01.tech.local" |
| ESXName | ESXi host name. | ESXName="esx01.tech.local" |
| FolderRef | Folder reference ID. | FolderRef="group-v01" |
| VmLocation | Machine location. | VmLocation="srv01.tech.local\" |
| VmName | Machine name. | VmName="VM01" |
| VmRef | Machine reference ID. | VmRef="vm-01" |
| VbrHostName | Backup server name. Can be a DNS name, an FQDN or an IP address. | VbrHostName="vbrsrv01.tech.local" |
| VbrVersion | Veeam Backup & Replication version. | VbrVersion="13.0.1.180" |
| Version | Event version (service parameter). | Version="1" |
| Description | Event message details. | Description="VM [VM01] validation task has finished with [Failed] state." |

Syslog Message Example

|  |
| --- |
| 1 2025-11-24T04:43:21.493700-07:00 VBRSRV01 Veeam\_MP - - [origin enterpriseId="31023"] [categoryId=0 instanceId=351 JobSessionID="4467f18a-d9e1-4fcf-ae1d-f635eb26cbe9" JobID="21874156-34b0-4316-94ae-fb05b2f67ec4" JobType="3" TaskSessionID="4cf4d768-18f6-4189-afa1-6f5375dd561c" TaskSessionType="1" Result="1" OibID="d844fe29-818d-4da6-8adb-f9b6759d241a" IsSureReplica="False" HostName="srv01.tech.local" ESXName="esx01.tech.local" FolderRef="group-v01" VmLocation="srv01.tech.local\" VmName="VM01" VmRef="vm-01" VbrHostName="vbrsrv01.tech.local" VbrVersion="13.0.1.180" Version="1" Description="VM [VM01] validation task has finished with [Failed] state."] |


