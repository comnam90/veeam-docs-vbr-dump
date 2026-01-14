---
title: "VBREntraIDTenantBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrentraidtenantbackupjob.html"
last_updated: "1/28/2025"
product_version: "13.0.1.1071"
---

# VBREntraIDTenantBackupJob

In this article

Contains settings of a backup job for a Microsoft Entra ID tenant.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Id | Guid | Backup job ID. |
| Name | String | Backup job name. |
| Description | String | Backup job description. |
| Tenant | VBREntraIDTenant | Protected Microsoft Entra ID tenant. |
| RetentionType | VBRRetentionType | Retention type for the backup job. |
| RetentionPolicy | Int32 | Retention policy in days. |
| NotificationOptions | [VBRNotificationOptions](vbrnotificationoptions.md) | Notification options. |
| EnableSchedule | Boolean | Defines if the backup jobs runs by a schedule. |
| ScheduleOptions | ScheduleOptions | Schedule options. |
| ParentScheduleId | Guid | ID of the job after which the backup job is scheduled to be run. |
| EncryptionOptions | [VBREncryptionOptions](vbrencryptionoptions.md) | Encryption options. |

Related Commands

* [Add-VBREntraIDTenantBackupJob](add-vbrentraidtenantbackupjob.md)
* [Get-VBREntraIDTenantBackupJob](get-vbrentraidtenantbackupjob.md)
* [Set-VBREntraIDTenantBackupJob](set-vbrentraidtenantbackupjob.md)

Page updated 1/28/2025

Page content applies to build 13.0.1.1071
