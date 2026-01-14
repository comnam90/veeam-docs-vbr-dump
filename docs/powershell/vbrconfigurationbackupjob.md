---
title: "VBRConfigurationBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrconfigurationbackupjob.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRConfigurationBackupJob

In this article

Contains configuration backup job.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Enabled | bool | Indicates if the job is enabled (TRUE) or not (FALSE). |
| Repository | CBackupRepository | Target backup repository. |
| ScheduleOptions | [VBRConfigurationBackupScheduleOptions](vbrconfigurationbackupscheduleoptions.md) | Configuration backup job schedule settings. |
| RestorePointsToKeep | int | Number of restore points that must be kept. |
| EncryptionOptions | [VBREncryptionOptions](vbrencryptionoptions.md) | Data encryption options applied to the configuration backup job. |

Related Commands

* [Get-VBRConfigurationBackupJob](get-vbrconfigurationbackupjob.md)
* [Set-VBRConfigurationBackupJob](set-vbrconfigurationbackupjob.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
