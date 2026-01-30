---
title: "Set-VBRBackupToTapeJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrbackuptotapejob.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Set-VBRBackupToTapeJob


Short Description

Modifies a backup to tape job or a GFS job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify all kinds of tape jobs without editing media pools.

|  |
| --- |
| Set-VBRBackupToTapeJob -Job <VBRBackupToTapeJob> [-Name <string>] [-Description <string>] [-EjectCurrentMedium] [-ExportCurrentMediaSet] [-ExportDays <DayOfWeek[]> {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-FullBackupPolicy <VBRFullBackupToTapePolicy>] [-ScheduleOptions <VBRBackupToTapeScheduleOptions>] [-Object <Object[]>] [-ProcessIncrementalBackup] [-UseHardwareCompression] [-WaitPeriod <timespan>] [-WaitForBackupJob] [-NotificationOptions <VBRNotificationOptions>] [-JobScriptOptions <VBRJobScriptOptions>] [-AlwaysCopyFromLatestFull] [-PassThru] [-Force] [-EnableParallelDrivesUsage] [-LimitTapeDrives <Int32>] [-PreventInterruption]  [<CommonParameters>] |

* Modify a tape job targeted to a non-GFS media pool.

|  |
| --- |
| Set-VBRBackupToTapeJob -Job <VBRBackupToTapeJob> [-Name <string>] [-Description <string>] [-EjectCurrentMedium] [-ExportCurrentMediaSet] [-FullBackupMediaPool <VBRTapeMediaPool>] [-IncrementalBackupMediaPool <VBRTapeMediaPoolBase>] [-ExportDays <DayOfWeek[]> {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-FullBackupPolicy <VBRFullBackupToTapePolicy>] [-ScheduleOptions <VBRBackupToTapeScheduleOptions>] [-Object <Object[]>] [-ProcessIncrementalBackup] [-UseHardwareCompression] [-WaitPeriod <timespan>] [-WaitForBackupJob] [-NotificationOptions <VBRNotificationOptions>] [-JobScriptOptions <VBRJobScriptOptions>] [-AlwaysCopyFromLatestFull] [-PassThru] [-Force] [-EnableParallelDrivesUsage] [-LimitTapeDrives <Int32>] [-PreventInterruption]  [<CommonParameters>] |

* Modify a tape job targeted to a GFS media pool.

|  |
| --- |
| Set-VBRBackupToTapeJob -Job <VBRBackupToTapeJob> [-Name <string>] [-Description <string>] [-EjectCurrentMedium] [-ExportCurrentMediaSet] [-GFSMediaPool <VBRTapeGFSMediaPool>] [-ExportDays <DayOfWeek[]> {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-FullBackupPolicy <VBRFullBackupToTapePolicy>] [-ScheduleOptions <VBRBackupToTapeScheduleOptions>] [-Object <Object[]>] [-ProcessIncrementalBackup] [-UseHardwareCompression] [-WaitPeriod <timespan>] [-WaitForBackupJob] [-NotificationOptions <VBRNotificationOptions>] [-JobScriptOptions <VBRJobScriptOptions>] [-AlwaysCopyFromLatestFull] [-GFSScheduleOptions <VBRTapeGFSScheduleOptions>] [-PassThru] [-Force] [-EnableParallelDrivesUsage] [-LimitTapeDrives <Int32>] [-PreventInterruption]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies a selected backup to tape job or a GFS job.

|  |
| --- |
| ![Set-VBRBackupToTapeJob](images/icon_note.webp) Note: |
| Consider the following:   * To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameters values with new values. The parameters that you omit will remain unchanged. * The cmdlet checks if the data of the VMs added to the job changes its geographic location. * The cmdlet will not run if the geographic location of the repository where VM backups reside and the target media pool location do not match. If you still want to run the cmdlet, use the Force parameter. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the backup to tape job to which you want to apply new settings. | Accepts the following objects:   * GUID * String * [VBRBackupToTapeJob](vbrbackuptotapejob.md). To get this object, run the [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. * TapeJob. To get this object, run the [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the name you want to assign to the backup to tape job. | String | False | Named | False |
| Description | Specifies the description of the backup to tape job. | String | False | Named | False |
| EjectCurrentMedium | Defines that the tapes will be automatically ejected from drive after the job finishes.  The ejected tape is moved to a standard library slot. | SwitchParameter | False | Named | False |
| ExportCurrentMediaSet | Defines that the tapes belonging to the media set will be automatically placed to Import/Export (Mail) slot for further export. Use the ExportDays parameter to set days on which you want to export tapes.  If you use this parameter, but do not set the ExportDays parameter, the tapes will be exported every day. | SwitchParameter | False | Named | False |
| FullBackupMediaPool | For non-GFS jobs.  Specifies the media pool where you want to store full backups produced by this tape job. | Accepts the [VBRTapeMediaPool](vbrtapemediapool.md) object, GUID or string. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | True | Named | False |
| IncrementalBackupMediaPool | For non-GFS jobs.  Used to set media pool for the ProcessIncrementalBackup parameter.  Specifies the media pool where you want to store incremental backups produced by this tape job. | Accepts the [VBRTapeMediaPoolBase](vbrtapemediapoolbase.md) object, GUID or string. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | False | Named | False |
| GFSMediaPool | For GFS jobs.  Specifies the target GFS media pool. | Accepts the [VBRTapeGFSMediaPool](vbrtapegfsmediapool.md) object, GUID or string. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | True | Named | False |
| ExportDays | Used to set days for exporting tapes for the ExportCurrentMediaSet parameter.  Specifies days on which the tapes written by this tape job will be automatically exported: Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday. | DayOfWeek[] | False | Named | False |
| FullBackupPolicy | Specifies virtualized synthetic full backup for tape settings. | Accepts the [VBRFullBackupToTapePolicy](vbrfullbackuptotapepolicy.md) object. To create this object, run the [New-VBRFullBackupToTapePolicy](new-vbrfullbackuptotapepolicy.md) cmdlet. | False | Named | False |
| ScheduleOptions | Specifies backup to tape job schedule.  Default:   * Enabled: False * Type: Daily * DailyOptions: Type: SelectedDays, Period: 18:00, DayOfWeek: Saturday * MonthlyOptions: Period: 22:00, DayNumberInMonth: Fourth, DayOfWeek: Saturday, Months: January, February, March, April, May, June, July, August, September, October, November, December * ScheduleOptions: From Sunday to Saturday, from 00:00 to 23:00, Enabled: True * JobId: Null | Accepts the [VBRBackupToTapeScheduleOptions](vbrbackuptotapescheduleoptions.md) object. To create this object, run the [New-VBRBackupToTapeScheduleOptions](new-vbrbackuptotapescheduleoptions.md) cmdlet. | False | Named | False |
| Object | Specifies the array of backup to tape job sources. Tape job sources are backup jobs or backup repositories. | Accepts either of the following types:   * [VBRCloudTenant](vbrcloudtenant.md). To get this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. * CBackupJob. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. * [VBREPJob](vbrepjob.md). To get this object, run the [Get-VBREPJob](get-vbrepjob.md) cmdlet. * CBackupRepository. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. * [VBRCloudTenantResource](vbrcloudtenantresource.md). To create this object, run the [New-VBRCloudTenantResource](new-vbrcloudtenantresource.md) cmdlet. | False | Named | False |
| ProcessIncrementalBackup | Defines that this tape job will archive incremental backups.  Use the IncrementalBackupMediaPool parameter to specify a separate media pool for storing incremental backups. If you do not set the IncrementalBackupMediaPool parameter, incremental backups will be stored to the media pool you set for full backups. | SwitchParameter | False | Named | False |
| UseHardwareCompression | Defines that tape library must perform hardware compression for archives. Do not use this option for archiving Veeam backups or other already compressed files. | SwitchParameter | False | Named | False |
| WaitPeriod | Used to set time period for the WaitForBackupJob parameter.  Specifies the time period for which the tape job must wait for the source backup jobs to finish.  Allowed values: 1-777 minutes. | Accepts TimeSpan, int or string. | False | Named | False |
| WaitForBackupJob | Defines that the tape job must wait for the source backup job to finish. Use the WaitPeriod parameter to set the time period. | SwitchParameter | False | Named | False |
| NotificationOptions | Specifies the email notification options. | Accepts the [VBRNotificationOptions](vbrnotificationoptions.md) object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| JobScriptOptions | Specifies scripting options. | Accepts the [VBRJobScriptOptions](vbrjobscriptoptions.md) object. To create this object, run the [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md) cmdlet. | False | Named | False |
| AlwaysCopyFromLatestFull | Defines that on each run the tape job must copy only the latest backup chain. Otherwise, on each run the tape job will copy all restore points produced by the source backup jobs that are available on disk. | SwitchParameter | False | Named | False |
| GFSScheduleOptions | Specifies the schedule settings for the GFS media pool. | Accepts the [VBRTapeGFSScheduleOptions](vbrtapegfsscheduleoptions.md) object. To create this object, run the [New-VBRTapeGFSScheduleOptions](new-vbrtapegfsscheduleoptions.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will create a job even if the geographic location of the repositories where VM backups reside and the target media pool location do not match. | SwitchParameter | False | Named | False |
| EnableParallelDrivesUsage | Enables parallel processing of media pools.  Default: False. | SwitchParameter | False | Named | False |
| LimitTapeDrives | Defines that the cmdlet will limit the number of drives to use for processing this tape job.  Default: 2 drives. | Int32 | False | Named | False |
| PreventInterruption | Defines that, if the source job starts while the tape job is still running, the source job will be placed on hold instead of interrupting the tape job and resulting in incomplete tape backups.  Using this option may result in source backup jobs starting significantly later than their scheduled start time, thus potentially missing recovery point objectives. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRBackupToTapeJob](vbrbackuptotapejob.md)

Examples

Changing Media Pool for Backup to Tape Job  [Using Pipeline]

This example shows how to set a new media pool for the incremental backups.

|  |
| --- |
| $newpool = Get-VBRTapeMediaPool -Name "Incremental Backups"  Get-VBRTapeJob -Name "Daily WebApp Backup" | Set-VBRBackupToTapeJob -IncrementalBackupMediaPool $newpool |

Perform the following steps:

1. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save the result to the $newpool variable.
2. Run the [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. Specify the Name parameter value. Pipe the cmdlet output to the Set-VBRBackupToTapeJob cmdlet. Set the $newpool variable as the IncrementalBackupMediaPool parameter value.

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Get-VBREPJob](get-vbrepjob.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRTapeMediaPool](get-vbrtapemediapool.md)
* [New-VBRFullBackupToTapePolicy](new-vbrfullbackuptotapepolicy.md)
* [New-VBRBackupToTapeScheduleOptions](new-vbrbackuptotapescheduleoptions.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [New-VBRNotificationOptions](new-vbrnotificationoptions.md)
* [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md)
* [Get-VBRLocation](get-vbrlocation.md)


