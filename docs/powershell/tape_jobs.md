---
title: "Tape Jobs"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/tape_jobs.html"
last_updated: "12/16/2025"
product_version: "13.0.1.1071"
---

# Tape Jobs


You can create and manage tape jobs from your command line. For more information on how to enable, copy and remove tape jobs using cmdlets, see the [Working with Jobs](working_with_jobs.md) section.

|  |
| --- |
| ![Tape Jobs](images/icon_important.webp) Important! |
| Veeam PowerShell terminates support for restoring from tape archives. The tape restore cmdlets are obsolete. They will work, but it is recommended to perform the tape restore operation with Veeam Backup & Replication UI for full functionality. |

You can use the cmdlets from this section to perform the following operations with tape jobs:

Tape Jobs

| Cmdlet | Operation |
| --- | --- |
| [Add-VBRBackupToTapeJob](add-vbrbackuptotapejob.md) | Creates a backup to tape job or a GFS job. |
| [Add-VBRFileToTapeJob](add-vbrfiletotapejob.md) | Creates a file to tape job. |
| [Add-VBRObjectToTapeJob](add-vbrobjecttotapejob.md) | Creates an object to tape job. |
| [Get-VBRTapeJob](get-vbrtapejob.md) | Returns tape jobs. |
| [New-VBRFileToTapeObject](new-vbrfiletotapeobject.md) | Creates an object containing files for file to tape job. |
| [Set-VBRBackupToTapeJob](set-vbrbackuptotapejob.md) | Modifies a selected backup to tape job or a GFS job. |
| [Set-VBRFileToTapeJob](set-vbrfiletotapejob.md) | Modifies a selected file to tape job. |
| [Set-VBRObjectToTapeJob](set-vbrobjecttotapejob.md) | Modifies a selected object to tape job. |
| [Sync-VBRBackupToTapeJob](sync-vbrbackuptotapejob.md) | Creates an active full backup for GFS job. |
| [Sync-VBRObjectToTapeJob](sync-vbrobjecttotapejob.md) | Starts an active full for a selected GFS object to tape job. |
| [Get-VBRTapeRestoreAllContentDependentMedium](get-vbrtaperestoreallcontentdependentmedium.md) | Returns dependent tapes. |
| [Start-VBRTapeRestoreAllContent](start-vbrtaperestoreallcontent.md) | Starts restore of the content of the entire tape. |
| [Start-VBRTapeObjectStorageRestore](start-vbrtapeobjectstoragerestore.md) | Starts restore of the objects backed up to tape. |
| [Find-VBRTapeCatalogItem](find-vbrtapecatalogitem.md) | Looks for files or folders backed-up by tape jobs. |
| [Find-VBRTapeCatalogItemVersion](find-vbrtapecatalogitemversion.md) | Looks for backed up versions of a file or folder. |
| [Start-VBRTapeFileRestore](start-vbrtapefilerestore.md) | Starts the restore of files and folders from tape. |
| [Get-VBRTapeBackupSession](get-vbrtapebackupsession.md) | Returns tape backup job sessions. |

Tape Jobs Schedule

| Cmdlet | Operation |
| --- | --- |
| [New-VBRBackupToTapeScheduleOptions](new-vbrbackuptotapescheduleoptions.md) | Creates schedule for tape jobs or GFS jobs. |
| [New-VBRFileToTapeBackupPolicy](new-vbrfiletotapebackuppolicy.md) | Creates schedule for file to tape job. |
| [New-VBRFullBackupToTapePolicy](new-vbrfullbackuptotapepolicy.md) | Creates virtual full schedule. |
| [New-VBRTapeGFSScheduleOptions](new-vbrtapegfsscheduleoptions.md) | Creates GFS schedule. |
| [Set-VBRTapeGFSScheduleOptions](set-vbrtapegfsscheduleoptions.md) | Modifies GFS schedule. |


