---
title: "VBREntraIDLogsBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrentraidlogsbackupjob.html"
last_updated: "7/28/2025"
product_version: "13.0.1.1071"
---

# VBREntraIDLogsBackupJob

In this article

Contains details on a backup job for Microsoft Entra ID audit and sign-in logs.

Properties

| Property | Type | Description |
| --- | --- | --- |
| BackupObject | VBREntraIdLogsBackupJobObject | Information about the tenant whose logs are backed up. |
| Id | Guid | Backup job ID. |
| Name | String | Backup job name. |
| Description | String | Backup job description. |
| ShortTermBackupRepository | CBackupRepository | Primary log backup repository. |
| ShortTermRetentionType | VBREntraIdLogsBackupShortTermRetentionType | Retention type for the backup job. |
| ShortTermRetentionPeriod | Int32 | Retention period. |
| SecondaryTargetEnabled | Boolean | Defines if the job creates additional copies of the backups. |
| SecondaryTarget | VBRUnstructuredBackupSecondaryTarget[] | Secondary log backup repository that keeps additional backup copies. |
| StorageOptions | VBRStorageOptions | Storage settings of the backup job. |
| HealthCheckOptions | VBRFullBackupOptions | Health check settings of the backup job. |
| NotificationOptions | [VBRNotificationOptions](vbrnotificationoptions.md) | Notification settings of the backup job. |
| ScriptOptions | [VBRJobScriptOptions](vbrjobscriptoptions.md) | Script settings of the backup job. |
| SecurityProcessingMode | VBRUnstructuredBackupSecurityProcessingMode | Defines if attribute changes are tracked for files and folders (2), for folders only (1), or not tracked at all (0). |
| ScheduleEnabled | Boolean | Defines if the backup jobs runs by a schedule. |
| ScheduleOptions | VBRServerScheduleOptions | Settings of the backup job schedule. |
| IsHighPriority | Boolean | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it first. |

Related Commands

* [Add-VBREntraIDLogsBackupJob](add-vbrentraidlogsbackupjob.md)
* [Get-VBREntraIDLogsBackupJob](get-vbrentraidlogsbackupjob.md)
* [Set-VBREntraIDLogsBackupJob](set-vbrentraidlogsbackupjob.md)

Page updated 7/28/2025

Page content applies to build 13.0.1.1071
