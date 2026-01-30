---
title: "VBRFileToTapeJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrfiletotapejob.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# VBRFileToTapeJob


Contains file to tape job.

Properties

"?" indicates that the property accepts zero values.

| Property | Type | Description |
| --- | --- | --- |
| FullBackupPolicy | [VBRFullBackupToTapePolicy](vbrfullbackuptotapepolicy.md) | The virtual full backup creation policy. |
| IncrementalBackupPolicy | [VBRFileToTapeBackupPolicy](vbrfiletotapebackuppolicy.md) | The job schedule for creating incremental backups. |
| Object | [VBRFileToTapeObject](vbrfiletotapeobject.md)[] | The file system object set as the source for the tape job. |
| UseVss | bool | Indicates that Microsoft VSS must be used to place the files that are locked by running applications to tape in a consistent state. |
| EjectCurrentMedium | bool | Indicates if the tape currently used by the tape job must be ejected. |
| ExportCurrentMediaSet | bool | Indicates if the current media set created by the tape job must be exported when it is complete. |
| ExportDays | DayOfWeek[] | Days on which the media sets must be exported. |
| FullBackupMediaPool | [VBRTapeMediaPool](vbrtapemediapool.md) | The media pool for full backups. |
| IncrementalBackupMediaPool | [VBRTapeMediaPool](vbrtapemediapool.md) | The media pool for incremental backups. |
| UseHardwareCompression | bool | Indicates if the tape library hardware compression must be used. |
| NextRun | DateTime? | The date and time of the next run of the job. |
| Target | Object | The media pool used by the job. |
| Type | [VBRJobType](vbrjob.md) | Job type: FileToTape. |
| LastResult | [VBRSessionResult](enums.md#vbrsessionresult) | Session result. |
| LastState | [VBRSessionState](enums.md#vbrsessionstate) | Session state. |
| Id | GUID | The unique identifier of the job. |
| Name | string | The name of the job. |
| Description | string | The description of the job. |
| NotificationOptions | [VBRNotificationOptions](vbrnotificationoptions.md) | Email notification options applied to this job. |
| JobScriptOptions | [VBRJobScriptOptions](vbrjobscriptoptions.md) | Script options applied to this job. |

Related Commands

* [Add-VBRFileToTapeJob](add-vbrfiletotapejob.md)
* [Get-VBRTapeJob](get-vbrtapejob.md)
* [Set-VBRFileToTapeJob](set-vbrfiletotapejob.md)


