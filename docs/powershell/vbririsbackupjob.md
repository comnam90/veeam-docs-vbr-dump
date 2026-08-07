---
title: "VBRIrisBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbririsbackupjob.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# VBRIrisBackupJob


Contains an InterSystems IRIS application backup policy.

VBRIrisBackupJob

| Property | Type | Description |
| Id | Guid | Specifies the ID of the application backup policy. |
| Name | String | Specifies the name of the application backup policy. |
| Description | String | Specifies the description of the application backup policy. |
| ApplicationType | VBRApplicationType | Specifies the application type of the policy. |
| BackupObject | Object[] | Specifies the array of InterSystems IRIS instances and protection groups added to the policy. |
| ExcludedObject | VBRDiscoveredIris[] | Specifies the array of InterSystems IRIS instances excluded from the policy. |
| SourceBackup | CBackup | Specifies the backup mapped to the policy. |
| BackupProxy | VBRNASProxyServer[] | Specifies the array of backup proxies used by the policy. |
| BackupRepository | CBackupRepository | Specifies the target backup repository of the policy. |
| RetentionPolicy | Int32 | Specifies the number of restore points kept on the backup repository. |
| SnapshotImmutabilityEnabled | Boolean | Specifies whether immutability is enabled for snapshots. |
| SnapshotImmutabilityPeriod | Int32 | Specifies the number of days during which snapshots remain immutable. |
| SnapshotRetentionEnabled | Boolean | Specifies whether a separate retention policy for snapshots is enabled. |
| SnapshotRetentionPeriod | Int32 | Specifies the number of days during which snapshots are retained. |
| StorageOptions | VBRStorageOptions | Specifies storage optimization settings of the policy. |
| ProcessingOptions | [VBRIrisProcessingOptions[]](vbririsprocessingoptions.md) | Specifies processing settings for the InterSystems IRIS instances added to the policy. |
| HealthCheckOptions | VBRHealthCheckOptions | Specifies the health check schedule of the policy. |
| NotificationOptions | VBRNotificationOptions | Specifies notification settings of the policy. |
| ScriptOptions | VBRJobScriptOptions | Specifies pre-job and post-job script options of the policy. |
| ScheduleEnabled | Boolean | Specifies whether the policy is scheduled to run automatically. |
| ScheduleOptions | VBRServerScheduleOptions | Specifies the schedule settings of the policy. |
| GfsOptions | VBRComputerGFSOptions | Specifies GFS (grandfather-father-son) retention policy settings of the policy. |
| GfsRetentionEnabled | Boolean | Specifies whether the GFS retention policy is enabled. |
| IsHighPriority | Boolean | Specifies whether the policy has higher priority for resource allocation. |
| JobEnabled | Boolean | Specifies whether the policy is enabled. |

Related Commands

* [Add-VBRIrisBackupJob](add-vbririsbackupjob.md)
* [Set-VBRIrisBackupJob](set-vbririsbackupjob.md)
* [Get-VBRApplicationBackupJob](get-vbrapplicationbackupjob.md)

Page updated 2026-06-10

