---
title: "Set-VBRFileToTapeJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrfiletotapejob.html"
last_updated: "12/4/2025"
product_version: "13.0.1.1071"
---

# Set-VBRFileToTapeJob


Short Description

Modifies a file to tape job or a GFS file to tape job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify a file to tape job.

|  |
| --- |
| Set-VBRFileToTapeJob -Job <VBRFileToTapeJob> [-Name <String>] [-Description <String>] [-EjectCurrentMedium] [-ExportCurrentMediaSet] [-FullBackupMediaPool <VBRTapeMediaPool>] [-IncrementalBackupMediaPool <VBRTapeMediaPool>] [-ExportDays <DayOfWeek[]>] [-FullBackupPolicy <VBRFileToTapeBackupPolicy>] [-IncrementalBackupPolicy <VBRFileToTapeBackupPolicy>] [-Object <VBRFileToTapeObject[]>] [-NdmpObject <VBRNDMPVolume[]>] [-UseVSS] [-UseHardwareCompression] [-NotificationOptions] [-JobScriptOptions] [-PassThru] [-Force] [-EnableParallelDrivesUsage] [-LimitTapeDrives <Int32>] [-EnableFileAclChangeTracking]  [<CommonParameters>] |

* Modify a GFS file to tape job.

|  |
| --- |
| Set-VBRFileToTapeJob -Job <VBRFileToTapeJob> [-Name <string>] [-Description <string>] [-EjectCurrentMedium] [-ExportCurrentMediaSet] [-GFSMediaPool <VBRTapeGFSMediaPool>] [-GFSMediaSetsToExport {Daily | Weekly | Monthly | Quarterly | Yearly}] [-FullBackupPolicy <VBRFileToTapeBackupPolicy>] [-IncrementalBackupPolicy <VBRFileToTapeBackupPolicy>] [-Object <VBRFileToTapeObject[]>] [-NdmpObject <VBRNDMPVolume[]>] [-UseVSS] [-UseHardwareCompression] [-GFSScheduleOptions <VBRTapeGFSScheduleOptions>] [-NotificationOptions <VBRNotificationOptions>] [-JobScriptOptions <VBRJobScriptOptions>] [-PassThru] [-Force] [-EnableParallelDrivesUsage] [-LimitTapeDrives <int>] [-EnableFileAclChangeTracking] [<CommonParameters>] |

Detailed Description

This cmdlet modifies a selected file to tape job or GFS file to tape job that was created before.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the file to tape job to which you want to apply new settings. | Accepts the following objects:   * GUID * String * [VBRBackupToTapeJob](vbrbackuptotapejob.md). To get this object, run the [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. * TapeJob. To get this object, run the [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the name you want to assign to the file to tape job. | String | False | Named | False |
| Description | Specifies the description of the file to tape job. | String | False | Named | False |
| EjectCurrentMedium | Defines that the tapes will be automatically ejected from drive after the job finishes.  The ejected tape is moved to a standard library slot. | SwitchParameter | False | Named | False |
| ExportCurrentMediaSet | For non-GFS file to tape jobs.  Defines that the tapes belonging to the media set will be automatically placed to Import/Export (Mail) slot for further export. Use the ExportDays parameter to set days on which you want to export tapes.  If you use this parameter, but do not set the ExportDays parameter, the tapes will be exported every day. | SwitchParameter | False | Named | False |
| FullBackupMediaPool | For non-GFS file to tape jobs.  Specifies the media pool where you want to store full backups produced by this tape job. | Accepts the [VBRTapeMediaPool](vbrtapemediapool.md) object, GUID or string. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | True | Named | False |
| IncrementalBackupMediaPool | For non-GFS file to tape jobs.  Used to set media pool for the ProcessIncrementalBackup parameter.  Specifies the media pool where you want to store incremental backups produced by this tape job.  If you do not specify a media pool, incremental backups will be stored to the media pool you set for full backups. | Accepts the [VBRTapeMediaPoolBase](vbrtapemediapoolbase.md) object, GUID or string. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | False | Named | False |
| GFSMediaPool | For GFS file to tape jobs.  Specifies the target GFS media pool. | Accepts the [VBRTapeGFSMediaPool](vbrtapegfsmediapool.md) object, GUID or string. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | False | Named | False |
| ExportDays | For non-GFS file to tape jobs.  Used to set days for exporting tapes for the ExportCurrentMediaSet parameter.  Specifies days on which the tapes written by this tape job will be automatically exported: Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday. | DayOfWeek[] | False | Named | False |
| GFSMediaSetsToExport | For GFS file to tape jobs.  Specifies GFS media sets the tapes for which will be automatically exported once the tape job is finished:   * Daily * Weekly * Monthly * Quarterly * Yearly | VBRGFSMediaSetTypeToExport[] | False | Named | False |
| FullBackupPolicy | Specifies virtualized synthetic full backup for tape settings.  Default:   * Type: Daily * DailyOptions: Type: SelectedDays, Period: 18:00, DayOfWeek: Saturday * MonthlyOptions: Period: 22:00, DayNumberInMonth: Fourth, DayOfWeek: Saturday, Months: January, February, March, April, May, June, July, August, September, October, November, December * Enabled: false | Accepts the [VBRFullBackupToTapePolicy](vbrfullbackuptotapepolicy.md) object. to create this object, run the [New-VBRFullBackupToTapePolicy](new-vbrfullbackuptotapepolicy.md) cmdlet. | False | Named | False |
| IncrementalBackupPolicy | Specifies incremental backup settings.  Default:   * Type: Daily. * DailyOptions: Type: SelectedDays, Period: 18:00, DayOfWeek: Saturday. * MonthlyOptions: Period: 22:00, DayNumberInMonth: Fourth, DayOfWeek: Saturday, Months: January, February, March, April, May, June, July, August, September, October, November, December. * Enabled: False. | Accepts the [VBRFileToTapeBackupPolicy](vbrfiletotapebackuppolicy.md) object. To get this object, run the [New-VBRFileToTapeBackupPolicy](new-vbrfiletotapebackuppolicy.md) cmdlet. | False | Named | False |
| Object | Specifies the array of file to tape job sources. | Accepts the [VBRFileToTapeJob](vbrfiletotapejob.md) object. To get this object, run the [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. | False | Named | False |
| NdmpObject | Specifies the array of NDMP server volumes. | Accepts the VBRNDMPVolume[] object. To get this object, run the [Get-VBRNDMPVolume](get-vbrndmpvolume.md) cmdlet. | False | Named | False |
| UseVSS | Defines that the VSS (Microsoft Volume Shadow Copy) must be used.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| UseHardwareCompression | Defines that tape library must perform hardware compression for archives. Do not use this option for archiving Veeam backups or other already compressed files. | SwitchParameter | False | Named | False |
| GFSScheduleOptions | For GFS file to tape jobs.  Specifies the schedule settings for the GFS media pool. | Accepts the [VBRTapeGFSScheduleOptions](vbrtapegfsscheduleoptions.md) object. To create this object, run the [New-VBRTapeGFSScheduleOptions](new-vbrtapegfsscheduleoptions.md) cmdlet. | False | Named | False |
| NotificationOptions | Specifies the email notification options. | Accepts the [VBRNotificationOptions](vbrnotificationoptions.md) object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| JobScriptOptions | Specifies the scripting options. | Accepts the [VBRJobScriptOptions](vbrjobscriptoptions.md) object. To create this object, run the [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md) cmdlet. | False | Named | False |
| PassThru | Defines that the command returns the output object to the Windows PowerShell console. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will update a job even if the geographic location of the repositories where VM backups reside and the target media pool location do not match. | SwitchParameter | False | Named | False |
| EnableParallelDrivesUsage | Enables parallel processing of media pools.  Default: False. | SwitchParameter | False | Named | False |
| LimitTapeDrives | Defines that the cmdlet will limit the number of drives to use for processing this tape job.  Default: 2 drives. | Int32 | False | Named | False |
| EnableFileAclChangeTracking | Enables backup of permissions and attributes for files.  Default: False. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRFileToTapeJob](vbrfiletotapejob.md)

Examples

Changing Media Pool for File to Tape Job [Using Pipeline]

This example shows how to set a new media pool for the full backups for the File Backup to Tape job.

|  |
| --- |
| $newpool = Get-VBRTapeMediaPool -Name "File Backups"  Get-VBRTapeJob -Name "File Backup to Tape" | Set-VBRFileToTapeJob -FullBackupMediaPool $newpool |

Perform the following steps:

1. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save it to the $newpool variable.
2. Run the [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. Specify the Name parameter value.
3. Pipe the cmdlet output to the Set-VBRFileToTapeJob cmdlet. Set the $newpool variable as the FullBackupMediaPool parameter value.

Related Commands

* [Get-VBRTapeJob](get-vbrtapejob.md)
* [Get-VBRTapeMediaPool](get-vbrtapemediapool.md)
* [New-VBRFileToTapeBackupPolicy](new-vbrfiletotapebackuppolicy.md)
* [New-VBRFileToTapeObject](new-vbrfiletotapeobject.md)
* [New-VBRTapeGFSScheduleOptions](new-vbrtapegfsscheduleoptions.md)


