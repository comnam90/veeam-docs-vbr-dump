---
title: "VBRMongoDBBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrmongodbbackupjob.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# VBRMongoDBBackupJob

In this article

Contains MongoDB application backup policies.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | GUID | Unique MongoDB backup policy ID. |
| Name | String | MongoDB backup policy name. |
| Description | String | MongoDB backup policy description. |
| ApplicationType | VBRApplicationType | Type of application with a MongoDB backup policy. |
| BackupObject | Object[] | Array of discovered application entities: protection groups and replica sets. |
| SourceBackup | CBackup | Source backup for a MongoDB backup policy. |
| BackupRepository | CBackupRepository | Repository used for backup operations within MongoDB backup policies. |
| RetentionPolicy | Int32 | Retention policy for backups created by MongoDB backup. |
| StorageOptions | VBRStorageOptions | Storage options that you want to modify. |
| SyntheticFullOptions | VBRFullBackupOptions | Synthetic full backup schedule for MongoDB backup policies. |
| ActiveFullOptions | VBRFullBackupOptions | Active full backup schedule for MongoDB backup policies. |
| HealthCheckOptions | VBRHealthCheckOptions | Health check schedule options. |
| CompactFullOptions | VBRFullBackupOptions | Schedule for the compact operation of full backups created by the MongoDB backup policy. |
| NotificationOptions | VBRNotificationOptions | Notification settings for the application backup policy. |
| ProcessingOptions | [VBRMongoDBProcessingOptions[]](vbrmongodbprocessingoptions.md) | Processing settings for the application backup policy. |
| ScheduleEnabled | Boolean | Option to schedule the application backup policy to run on a regular basis. |
| ScheduleOptions | VBRServerScheduleOptions | Settings for the application backup policy schedule. |
| GFSOptions | VBRComputerGFSOptions | GFS retention settings for MongoDB backup policy. |
| GFSRetentionEnabled | Boolean | Enables GFS retention for MongoDB backup policy. |
| IsHighPriority | Boolean | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it first. |

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
