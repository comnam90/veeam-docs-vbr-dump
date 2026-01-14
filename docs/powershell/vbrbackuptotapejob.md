---
title: "VBRBackupToTapeJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrbackuptotapejob.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRBackupToTapeJob

In this article

Contains backup to tape job.

Properties

"?" indicates that the property accepts zero values.

| Property | Type | Description |
| --- | --- | --- |
| FullBackupPolicy | [VBRFullBackupToTapePolicy](vbrfullbackuptotapepolicy.md) | Virtual full backup creation policy. |
| Object | CBackupJob[] | Tape job source: backup job or backup repository. |
| ProcessIncrementalBackup | bool | Indicates if the incremental backups must be archived (TRUE) or not (FALSE). |
| ScheduleOptions | [VBRBackupToTapeScheduleOptions](vbrbackuptotapescheduleoptions.md) | Job schedule. |
| WaitForBackupJobs | bool | Indicates if the tape job must wait for the source backup job (TRUE) or not (FALSE). |
| WaitPeriod | TimeSpan | Time period for which the tape job waits for the source backup job. |
| EjectCurrentMedium | bool | Indicates if the tape currently used by the tape job must be ejected (TRUE) or not (FALSE). |
| ExportCurrentMediaSet | bool | Indicates if the current media set created by the tape job must be exported when it is complete (TRUE) or not (FALSE). |
| ExportDays | DayOfWeek[] | Days on which the media sets must be exported. |
| FullBackupMediaPool | [VBRTapeMediaPool](vbrtapemediapool.md) or [VBRTapeGFSMediaPool](vbrtapegfsmediapool.md) | Media pool for full backups or GFS media pool. |
| IncrementalBackupMediaPool | [VBRTapeMediaPool](vbrtapemediapool.md) | Media pool for incremental backups. |
| UseHardwareCompression | bool | Indicates if the tape library hardware compression must be used (TRUE) or not (FALSE). |
| NextRun | DateTime? | Date and time of the next run of the job. |
| Target | Object | Media pool used by the job. |
| Type | [VBRJobType](enums.md#vbrjobtype) | Job type: BackupToTape. |
| LastResult | [VBRSessionResult](enums.md#vbrsessionresult) | Session result. |
| LastState | [VBRSessionState](enums.md#vbrsessionstate) | Session state. |
| Id | GUID | Job ID. |
| Name | string | Job name. |
| Description | string | Job description. |
| AlwaysCopyFromLatestFull | bool | Indicates that on each run the job must copy only the last backup chain from disk (TRUE) or always copy all new restore point (FALSE). |
| GFSScheduleOptions | [VBRTapeGFSScheduleOptions](vbrtapegfsscheduleoptions.md) | Job GFS schedule. |
| NotificationOptions | [VBRNotificationOptions](vbrnotificationoptions.md) | Email notification options applied to the job. |
| JobScriptOptions | [VBRJobScriptOptions](vbrjobscriptoptions.md) | Script options applied to the job. |

Related Commands

[Add-VBRBackupToTapeJob](add-vbrbackuptotapejob.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
