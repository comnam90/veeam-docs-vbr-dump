---
title: "Add-VBRBackupToTapeJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrbackuptotapejob.html"
last_updated: "7/31/2025"
product_version: "13.0.1.1071"
---

# Add-VBRBackupToTapeJob

In this article

Short Description

Creates a backup to tape job or a GFS job.

Applies to

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Create a job targeted to a standard media pool.

|  |
| --- |
| Add-VBRBackupToTapeJob -Name <String> -FullBackupMediaPool <VBRTapeMediaPool> [-Force] [-AlwaysCopyFromLatestFull] [-CopyFromLatestFull] [-JobScriptOptions <VBRJobScriptOptions>] [-NotificationOptions <VBRNotificationOptions>] [-WaitForBackupJob] [-WaitPeriod <TimeSpan>] [-UseHardwareCompression] [-ProcessIncrementalBackup] [-Object <Object[]>] [-ScheduleOptions <VBRBackupToTapeScheduleOptions>] [-FullBackupPolicy <VBRFullBackupToTapePolicy>] [-ExportDays <DayOfWeek[]>] [-IncrementalBackupMediaPool <VBRTapeMediaPool>] [-ExportCurrentMediaSet] [-EjectCurrentMedium] [-Description <String>] [-EnableParallelDrivesUsage] [-LimitTapeDrives <Int32>] [-PreventInterruption]  [<CommonParameters>] |

* Create a GFS job.

|  |
| --- |
| Add-VBRBackupToTapeJob -Name <String> -GFSMediaPool <VBRTapeGFSMediaPool> [-Force] [-GFSScheduleOptions <VBRTapeGFSScheduleOptions>] [-AlwaysCopyFromLatestFull] [-CopyFromLatestFull] [-JobScriptOptions <VBRJobScriptOptions>] [-NotificationOptions <VBRNotificationOptions>] [-WaitForBackupJob] [-WaitPeriod <TimeSpan>] [-UseHardwareCompression] [-ProcessIncrementalBackup] [-Object <Object[]>] [-ScheduleOptions <VBRBackupToTapeScheduleOptions>] [-FullBackupPolicy <VBRFullBackupToTapePolicy>] [-ExportDays <DayOfWeek[]>] [-ExportCurrentMediaSet] [-EjectCurrentMedium] [-Description <String>] [-EnableParallelDrivesUsage] [-LimitTapeDrives <Int32>] [-PreventInterruption]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new backup to tape job or a GFS job. You can target the job to a simple or a GFS media pool.

|  |
| --- |
| ![Add-VBRBackupToTapeJob](images/icon_note.webp) Note: |
| Consider the following:   * The cmdlet checks if the data of the VMs added to the job changes its geographic location. * The cmdlet will not run if the geographic location of the repository where VM backups reside and the target media pool location do not match. If you still want to run the cmdlet, use the Force parameter. * If you choose to archive data from backup repositories, the backup to tape job will process only the backups that were created with backup jobs configured on this Veeam backup server. Imported backups and configuration backups will be skipped from processing. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name you want to assign to the backup to tape job. | String | True | Named | False |
| Description | Specifies the description of the backup to tape job. | String | False | Named | False |
| EjectCurrentMedium | Defines that the tapes will be automatically ejected from drive after the job finishes.  The ejected tape is moved to a standard library slot. | SwitchParameter | False | Named | False |
| ExportCurrentMediaSet | Defines that the tapes belonging to the media set will be automatically placed to Import/Export (Mail) slot for further export. Use the ExportDays parameter to set days on which you want to export tapes.  If you use this parameter, but do not set the ExportDays parameter, the tapes will be exported every day. | SwitchParameter | False | Named | False |
| FullBackupMediaPool | For non-GFS jobs.  Specifies the media pool where you want to store full backups produced by this tape job. | Accepts the [VBRTapeMediaPool](vbrtapemediapool.md) object, GUID or string. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | True | Named | False |
| IncrementalBackupMediaPool | For non-GFS jobs.  Used to set media pool for the ProcessIncrementalBackup parameter.  Specifies the media pool where you want to store incremental backups produced by this tape job. | Accepts the [VBRTapeMediaPool](vbrtapemediapool.md) object, GUID or string. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | False | Named | False |
| GFSMediaPool | For GFS jobs.  Specifies the target GFS media pool. | Accepts the [VBRTapeGFSMediaPool](vbrtapegfsmediapool.md) object, GUID or string. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | True | Named | False |
| ExportDays | Used to set days for exporting tapes for the ExportCurrentMediaSet parameter.  Specifies days on which the tapes written by this tape job will be automatically exported: Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday. | DayOfWeek[] | False | Named | False |
| FullBackupPolicy | Specifies virtual full settings. | Accepts the [VBRFullBackupToTapePolicy](vbrfullbackuptotapepolicy.md) object. To create this object, run the [New-VBRFullBackupToTapePolicy](new-vbrfullbackuptotapepolicy.md) cmdlet. | False | Named | False |
| ScheduleOptions | Specifies backup to tape job schedule.  Default:   * Enabled: False. * Type: Daily. * DailyOptions: Type: SelectedDays, Period: 18:00, DayOfWeek: Saturday. * MonthlyOptions: Period: 22:00, DayNumberInMonth: Fourth, DayOfWeek: Saturday, Months: January, February, March, April, May, June, July, August, September, October, November, December. * ScheduleOptions: From Sunday to Saturday, from 00:00 to 23:00, Enabled: True. * JobId: Null. | [VBRBackupToTapeScheduleOptions](vbrbackuptotapescheduleoptions.md) | False | Named | False |
| Object | Specifies the array of backup jobs or backup repositories that will be the source for this tape job. | Accepts one of the following objects:   * CBackupJob. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. * CBackupRepository. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. * VBRComputerBackupJob. To get this object, run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. * [VBREPJob](vbrepjob.md). To get this object, run the [Get-VBREPJob](get-vbrepjob.md) cmdlet. * [VBRCloudTenant](vbrcloudtenant.md). To get this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. * [VBRCloudTenantResource](vbrcloudtenantresource.md). To get this object, run the [New-VBRCloudTenantResource](new-vbrcloudtenantresource.md) cmdlet. | False | Named | False |
| ProcessIncrementalBackup | Defines that this tape job will archive incremental backups.  Use the IncrementalBackupMediaPool parameter to specify a separate media pool for storing incremental backups. If you do not set the IncrementalBackupMediaPool parameter, incremental backups will be stored to the media pool the you set for full backups. | SwitchParameter | False | Named | False |
| UseHardwareCompression | Defines that tape library must perform hardware compression for archives. Do not use this option for archiving Veeam backups or other already compressed files. | SwitchParameter | False | Named | False |
| WaitPeriod | Used to set time period for the WaitForBackupJob parameter.  Specifies the time period for which the tape job must wait for the source backup jobs to finish.  Allowed values: 1-777 minutes. | Accepts TimeSpan, int or string. | False | Named | False |
| WaitForBackupJob | Defines that the tape job must wait for the source backup job to finish. Use the WaitPeriod parameter to set the time period. | SwitchParameter | False | Named | False |
| NotificationOptions | Specifies the email notification options. | Accepts the [VBRNotificationOptions](vbrnotificationoptions.md) object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| JobScriptOptions | Specifies scripting options. | Accepts the [VBRJobScriptOptions](vbrjobscriptoptions.md) object. To create this object, run the [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md) cmdlet. | False | Named | False |
| CopyFromLatestFull | Defines that on the first run the tape job must copy only the latest backup chain. Otherwise,on the first run the job will copy all restore points produced by the source backup jobs that are available on disk. | SwitchParameter | False | Named | False |
| AlwaysCopyFromLatestFull | Defines that on each run the tape job must copy only the latest backup chain. Otherwise, on each run the tape job will copy all restore points produced by the source backup jobs that are available on disk. | SwitchParameter | False | Named | False |
| GFSScheduleOptions | Specifies the schedule settings for the GFS media pool. | Accepts the [VBRTapeGFSScheduleOptions](vbrtapegfsscheduleoptions.md) object. To create this object, run the [New-VBRTapeGFSScheduleOptions](new-vbrtapegfsscheduleoptions.md) cmdlet. | False | Named | False |
| EnableParallelDrivesUsage | Enables parallel processing of media pools.  Default: False. | SwitchParameter | False | Named | False |
| LimitTapeDrives | Defines that the cmdlet will limit the number of drives to use for processing this tape job.  Default: 2 drives. | Int32 | False | Named | False |
| PreventInterruption | Defines that, if the source job starts while the tape job is still running, the source job will be placed on hold instead of interrupting the tape job and resulting in incomplete tape backups.  Using this option may result in source backup jobs starting significantly later than their scheduled start time, thus potentially missing recovery point objectives. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will create a job even if the geographic location of the repositories where VM backups reside and the target media pool location do not match. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRBackupToTapeJob](vbrbackuptotapejob.md)

Examples

Creating Backup to Tape Job with Backup Job as Source

This example shows how to create a backup to tape job for SQL 1 Backup source job. The tape job will use the same media pool to back up full and incremental backups.

|  |
| --- |
| $job = Get-VBRJob -Name "SQL 1 Backup"  $mediapool = Get-VBRTapeMediaPool -Name "SQL Backups Media Pool"  $dailyoptions = New-VBRDailyOptions -DayOfWeek Friday -Period 23:00  $scheduleoptions = New-VBRBackupToTapeScheduleOptions -DailyOptions $dailyoptions -Enabled  Add-VBRBackupToTapeJob -Name "SQL to Tape" -Description "SQL archive" -Object $job -FullBackupMediaPool $mediapool -ProcessIncrementalBackup -IncrementalBackupMediaPool $mediapool -ExportDays Monday -ScheduleOptions $scheduleoptions |

Perform the following steps:

1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save the result to the $mediapool variable.
3. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Set Friday as the DayOfWeek parameter value and 23:00 as the Period parameter value. Save the result to the $dailyoptions variable.
4. Run the [New-VBRBackupToTapeScheduleOptions](new-vbrbackuptotapescheduleoptions.md) cmdlet. Set the $dailyoptions variable as the DailyOptions parameter value. Provide the Enabled parameter. Save the result to the $scheduleoptions variable.
5. Run the Add-VBRBackupToTapeJob cmdlet. Specify the following settings:

* Specify the Name and the Description parameter value.
* Set the $job variable as the Object parameter value.
* Set the $mediapool variable as the FullBackupMediaPool and IncrementalBackupMediaPool parameters value.
* Provide the ProcessIncrementalBackup parameter.
* Specify the ExportDays parameter value.
* Set the $scheduleoptions variable as the ScheduleOptions parameter value.

Related Commands

* [Get-VBRTapeMediaPool](get-vbrtapemediapool.md)
* [New-VBRFullBackupToTapePolicy](new-vbrfullbackuptotapepolicy.md)
* [New-VBRBackupToTapeScheduleOptions](new-vbrbackuptotapescheduleoptions.md)
* [Get-VBRJob](get-vbrjob.md)
* [Get-VBREPJob](get-vbrepjob.md)
* [New-VBRNotificationOptions](new-vbrnotificationoptions.md)
* [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md)
* [New-VBRBackupToTapeScheduleOptions](new-vbrbackuptotapescheduleoptions.md)
* [New-VBRTapeGFSScheduleOptions](new-vbrtapegfsscheduleoptions.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRLocation](get-vbrlocation.md)

Page updated 7/31/2025

Page content applies to build 13.0.1.1071
