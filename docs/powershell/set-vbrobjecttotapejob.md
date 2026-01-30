---
title: "Set-VBRObjectToTapeJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrobjecttotapejob.html"
last_updated: "7/22/2025"
product_version: "13.0.1.1071"
---

# Set-VBRObjectToTapeJob


Short Description

Modifies an object to tape job or GFS object to tape job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify an object to tape job.

|  |
| --- |
| Set-VBRObjectToTapeJob -Job <VBRObjectToTapeJob> [-Name <string>] [-Description <string>] [-EjectCurrentMedium] [-ExportCurrentMediaSet] [-FullBackupMediaPool <VBRTapeMediaPool>] [-IncrementalBackupMediaPool <VBRTapeMediaPool>] [-ExportDays {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-FullBackupPolicy <VBRFileToTapeBackupPolicy>] [-IncrementalBackupPolicy <VBRFileToTapeBackupPolicy>] [-Object <VBRObjectStorageBackupJobObject[]>] [-UseHardwareCompression] [-NotificationOptions <VBRNotificationOptions>] [-JobScriptOptions <VBRJobScriptOptions>] [-EnableFileAclChangeTracking]  [<CommonParameters>] |

* Modify a GFS object to tape job.

|  |
| --- |
| Set-VBRObjectToTapeJob -Job <VBRObjectToTapeJob> [-Name <string>] [-Description <string>] [-EjectCurrentMedium] [-ExportCurrentMediaSet] [-GFSMediaPool <VBRTapeGFSMediaPool>] [-GFSMediaSetsToExport {Daily | Weekly | Monthly | Quarterly | Yearly}] [-FullBackupPolicy <VBRFileToTapeBackupPolicy>] [-IncrementalBackupPolicy <VBRFileToTapeBackupPolicy>] [-Object <VBRObjectStorageBackupJobObject[]>] [-UseHardwareCompression] [-GFSScheduleOptions <VBRTapeGFSScheduleOptions>] [-NotificationOptions <VBRNotificationOptions>] [-JobScriptOptions <VBRJobScriptOptions>] [-EnableFileAclChangeTracking]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies a selected object to tape job or GFS object to tape job that was created before.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. This cmdlet will overwrite the previous parameter values with the new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the object to tape job to which you want to apply new settings. | Accepts the following objects:   * GUID * String * VBRObjectToTapeJob. To get this object, run the [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. | True | Named | False |
| Name | Specifies the name you want to assign to the object to tape job. | String | False | Named | False |
| Description | Specifies the description of the object to tape job. | String | False | Named | False |
| EjectCurrentMedium | Defines that the tapes will be automatically ejected from drive after the job finishes.  The ejected tape is moved to a standard library slot. | SwitchParameter | False | Named | False |
| ExportCurrentMediaSet | For non-GFS object to tape jobs.  Defines that the tapes belonging to the media set will be automatically placed to Import/Export (Mail) slot for further export. Use the ExportDays parameter to set days on which you want to export tapes.  If you use this parameter, but do not set the ExportDays parameter, the tapes will be exported every day. | SwitchParameter | False | Named | False |
| FullBackupMediaPool | For non-GFS object to tape jobs.  Specifies the media pool where you want to store full backups produced by this tape job. | Accepts the [VBRTapeMediaPool](vbrtapemediapool.md) object, GUID or string. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | True | Named | False |
| IncrementalBackupMediaPool | For non-GFS object to tape jobs.  Specifies the media pool where you want to store incremental backups produced by this tape job. | Accepts the [VBRTapeMediaPool](vbrtapemediapool.md) object, GUID or string. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | False | Named | False |
| GFSMediaPool | For GFS object to tape jobs.  Specifies the target GFS media pool. | Accepts the [VBRTapeGFSMediaPool](vbrtapegfsmediapool.md) object, GUID or string. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | False | Named | False |
| ExportDays | Used to set days for exporting tapes for the ExportCurrentMediaSet parameter.  Specifies days on which the tapes written by this tape job will be automatically exported: Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday. | DayOfWeek[] | False | Named | False |
| GFSMediaSetsToExport | For GFS object to tape jobs.  Specifies GFS media sets for which the tapes will be automatically exported once the tape job is finished:   * Daily * Weekly * Monthly * Quarterly * Yearly | VBRGFSMediaSetTypeToExport[] | False | Named | False |
| FullBackupPolicy | Specifies virtual synthetic full backup for tape settings.  Default:   * Type: Daily * DailyOptions: Type: SelectedDays, Period: 18:00, DayOfWeek: Saturday * MonthlyOptions: Period: 22:00, DayNumberInMonth: Fourth, DayOfWeek: Saturday, Months: January, February, March, April, May, June, July, August, September, October, November, December * Enabled: False | Accepts the [VBRFullBackupToTapePolicy](vbrfullbackuptotapepolicy.md) object. To create this object, run the [New-VBRFullBackupToTapePolicy](new-vbrfullbackuptotapepolicy.md) cmdlet. | False | Named | False |
| IncrementalBackupPolicy | Specifies the incremental backup settings.  Default:   * Type: Daily * DailyOptions: Type: SelectedDays, Period: 18:00, DayOfWeek: Saturday * MonthlyOptions: Period: 22:00, DayNumberInMonth: Fourth, DayOfWeek: Saturday, Months: January, February, March, April, May, June, July, August, September, October, November, December * Enabled: False | Accepts the [VBRFileToTapeBackupPolicy](vbrfiletotapebackuppolicy.md) object. To create this object, run the [New-VBRFileToTapeBackupPolicy](new-vbrfiletotapebackuppolicy.md) cmdlet. | False | Named | False |
| Object | Specifies the array of object to tape job sources. | Accepts the VBRObjectStorageBackupJobObject[] object, GUID or string. To create this object, run the [New-VBRObjectStorageBackupJobObject](new-vbrobjectstoragebackupjobobject.md) cmdlet. | True | Named | False |
| UseHardwareCompression | Defines that tape library must perform hardware compression for archives. Do not use this option for archiving Veeam backups or other already compressed files. | SwitchParameter | False | Named | False |
| GFSScheduleOptions | For GFS object to tape jobs.  Specifies the schedule settings for the GFS media pool. | Accepts the [VBRTapeGFSScheduleOptions](vbrtapegfsscheduleoptions.md) object. To create this object, run the [New-VBRTapeGFSScheduleOptions](new-vbrtapegfsscheduleoptions.md) cmdlet. | False | Named | False |
| NotificationOptions | Specifies the email notification options. | Accepts the [VBRNotificationOptions](vbrnotificationoptions.md) object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| JobScriptOptions | Specifies the scripting options. | Accepts the [VBRJobScriptOptions](vbrjobscriptoptions.md) object. To create this object, run the [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md) cmdlet. | False | Named | False |
| EnableFileAclChangeTracking | Enables backup of permissions and attributes for files.  Default: False. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRObjectToTapeJob](vbrobjecttotapejob.md)

Examples

Modifying Object to Tape Job [Using Pipeline]

This example shows how to set a new media pool for the incremental backups for the Sydney Container to Tape job.

|  |
| --- |
| $newpool = Get-VBRTapeMediaPool -Name "Azure Blob Storage Backups"  Get-VBRTapeJob -Name "Sydney Container to Tape" | Set-VBRObjectToTapeJob -IncrementalBackupMediaPool $newpool |

Perform the following steps:

1. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save the result to the $newpool variable.
2. Run the [Get-VBRTapeJob](get-vbrtapejob.md) cmdlet. Specify the Name parameter value.
3. Pipe the cmdlet output to the Set-VBRObjectToTapeJob cmdlet. Set the $newpool variable as the IncrementalBackupMediaPool parameter value.

Related Commands

* [Get-VBRTapeJob](get-vbrtapejob.md)
* [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)
* [New-VBRObjectStorageBackupJobObject](new-vbrobjectstoragebackupjobobject.md)
* [Get-VBRTapeMediaPool](get-vbrtapemediapool.md)
* [New-VBRFileToTapeBackupPolicy](new-vbrfiletotapebackuppolicy.md)
* [New-VBRNotificationOptions](new-vbrnotificationoptions.md)
* [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md)
* [New-VBRTapeGFSScheduleOptions](new-vbrtapegfsscheduleoptions.md)


