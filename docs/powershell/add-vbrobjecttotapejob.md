---
title: "Add-VBRObjectToTapeJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrobjecttotapejob.html"
last_updated: "12/19/2025"
product_version: "13.0.1.1071"
---

# Add-VBRObjectToTapeJob


Short Description

Creates an object to tape or GFS object to tape job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Create an object to tape job.

|  |
| --- |
| Add-VBRObjectToTapeJob -Name <string> -FullBackupMediaPool <VBRTapeMediaPool> -Object <VBRObjectStorageBackupJobObject[]> [-Description <string>] [-EjectCurrentMedium] [-ExportCurrentMediaSet] [-IncrementalBackupMediaPool <VBRTapeMediaPool>] [-ExportDays {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-FullBackupPolicy <VBRFileToTapeBackupPolicy>] [-IncrementalBackupPolicy <VBRFileToTapeBackupPolicy>] [-UseHardwareCompression] [-NotificationOptions <VBRNotificationOptions>] [-JobScriptOptions <VBRJobScriptOptions>] [-EnableFileAclChangeTracking]  [<CommonParameters>] |

* Create a GFS object to tape job.

|  |
| --- |
| Add-VBRObjectToTapeJob -Name <string> -GFSMediaPool <VBRTapeGFSMediaPool> -Object <VBRObjectStorageBackupJobObject[]> [-Description <string>] [-EjectCurrentMedium] [-ExportCurrentMediaSet] [-GFSMediaSetsToExport {Daily | Weekly | Monthly | Quarterly | Yearly}] [-FullBackupPolicy <VBRFileToTapeBackupPolicy>] [-IncrementalBackupPolicy <VBRFileToTapeBackupPolicy>] [-UseHardwareCompression] [-GFSScheduleOptions <VBRTapeGFSScheduleOptions>] [-NotificationOptions <VBRNotificationOptions>] [-JobScriptOptions <VBRJobScriptOptions>] [-EnableFileAclChangeTracking]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new object to tape or GFS object to tape job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name you want to assign to the object to tape job. | String | True | Named | False |
| Description | Specifies the description of the object to tape job. | String | False | Named | False |
| Object | Specifies the array of object to tape job sources. | Accepts the VBRObjectStorageBackupJobObject[] object, GUID or string. To create this object, run the [New-VBRObjectStorageBackupJobObject](new-vbrobjectstoragebackupjobobject.md) cmdlet. | True | Named | False |
| EjectCurrentMedium | Defines that the tapes will be automatically ejected from drive after the job finishes.  The ejected tape is moved to a standard library slot. | SwitchParameter | False | Named | False |
| ExportCurrentMediaSet | For non-GFS object to tape jobs.  Defines that the tapes belonging to the media set will be automatically placed to Import/Export (Mail) slot for further export. Use the ExportDays parameter to set days on which you want to export tapes.  If you use this parameter, but do not set the ExportDays parameter, the tapes will be exported every day. | SwitchParameter | False | Named | False |
| FullBackupMediaPool | For non-GFS object to tape jobs.  Specifies the media pool where you want to store full backups produced by this tape job. | Accepts the [VBRTapeMediaPool](vbrtapemediapool.md) object, GUID or string. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | True | Named | False |
| IncrementalBackupMediaPool | For non-GFS object to tape jobs.  Specifies the media pool where you want to store incremental backups produced by this tape job. | Accepts the [VBRTapeMediaPool](vbrtapemediapool.md) object, GUID or string. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | False | Named | False |
| GFSMediaPool | For GFS object to tape jobs.  Specifies the target GFS media pool. | Accepts the [VBRTapeGFSMediaPool](vbrtapegfsmediapool.md) object, GUID or string. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | True | Named | False |
| ExportDays | Used to set days for exporting tapes for the ExportCurrentMediaSet parameter.  Specifies days on which the tapes written by this tape job will be automatically exported: Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday. | DayOfWeek[] | False | Named | False |
| GFSMediaSetsToExport | For GFS object to tape jobs.  Specifies GFS media sets for which the tapes will be automatically exported once the tape job is finished:   * Daily * Weekly * Monthly * Quarterly * Yearly | VBRGFSMediaSetTypeToExport[] | False | Named | False |
| FullBackupPolicy | Specifies virtual synthetic full backup for tape settings.  Default:   * Type: Daily * DailyOptions: Type: SelectedDays, Period: 18:00, DayOfWeek: Saturday * MonthlyOptions: Period: 22:00, DayNumberInMonth: Fourth, DayOfWeek: Saturday, Months: January, February, March, April, May, June, July, August, September, October, November, December * Enabled: False | Accepts the [VBRFullBackupToTapePolicy](vbrfullbackuptotapepolicy.md) object. To create this object, run the [New-VBRFullBackupToTapePolicy](new-vbrfullbackuptotapepolicy.md) cmdlet. | False | Named | False |
| IncrementalBackupPolicy | Specifies incremental backup settings.  Default:   * Type: Daily * DailyOptions: Type: SelectedDays, Period: 18:00, DayOfWeek: Saturday * MonthlyOptions: Period: 22:00, DayNumberInMonth: Fourth, DayOfWeek: Saturday, Months: January, February, March, April, May, June, July, August, September, October, November, December * Enabled: False | Accepts the [VBRFileToTapeBackupPolicy](vbrfiletotapebackuppolicy.md) object. To create this object, run the [New-VBRFileToTapeBackupPolicy](new-vbrfiletotapebackuppolicy.md) cmdlet. | False | Named | False |
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

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Object to Tape Job

|  |  |
| --- | --- |
| This example shows how to create an object to tape job that backs up the Sydney Container Microsoft Azure container. The full backup runs every last Sunday of the month and incremental backups run daily at 22:00.  |  | | --- | | $server = Get-VBRUnstructuredServer -Name "Azure Blob Storage"  $object = New-VBRObjectStorageBackupJobObject -Server $server -Container "Sydney Container"  $mediapool = Get-VBRTapeMediaPool -Name "Object Storage Backup Media Pool"  $monthlyoptions = New-VBRMonthlyOptions -DayNumberInMonth Last -DayOfWeek Sunday -Period 22:00  $monthlypolicy = New-VBRFileToTapeBackupPolicy -Type Monthly -MonthlyOptions $monthlyoptions -Enabled  $dailyoptions = New-VBRDailyOptions -Type Everyday -Period 22:00  $dailypolicy = New-VBRFileToTapeBackupPolicy -Type Daily -DailyOptions $dailyoptions -Enabled  Add-VBRObjectToTapeJob -Name "Sydney Container to Tape" -Description "Backing up Sydney Azure Container" -Object $object -FullBackupMediaPool $mediapool -FullBackupPolicy $monthlypolicy -IncrementalBackupMediaPool $mediapool -IncrementalBackupPolicy $dailypolicy |  Perform the following steps:   1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [New-VBRObjectStorageBackupJobObject](new-vbrobjectstoragebackupjobobject.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Container parameter value. Save the result to the $object variable. 3. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save the result to the $mediapool variable. 4. Run the [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md) cmdlet. Set Last as the DayNumberInMonth parameter value and Sunday as the DayOfWeek parameter value. Specify the Period parameter. Save the result to the $monthlyoptions variable. 5. Run the [New-VBRFileToTapeBackupPolicy](new-vbrfiletotapebackuppolicy.md) cmdlet. Set Monthly as the Type parameter value. Set the $monthlyoptions variable as the MonthlyOptions parameter value. Provide the Enabled parameter. Save the result to the $monthlypolicy variable. 6. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Set Everyday as the Type parameter value and 22:00 as the Period parameter value. Save the result to the $dailyoptions variable. 7. Run the [New-VBRFileToTapeBackupPolicy](new-vbrfiletotapebackuppolicy.md) cmdlet. Set Daily as the Type parameter value. Set the $dailyoptions variable as the DailyOptions parameter value. Provide the Enabled parameter. Save the result to the $dailypolicy variable. 8. Run the Add-VBRObjectToTapeJob cmdlet. Specify the following settings:  * Specify the Name and the Description parameter values. * Set the $object variable as the Object parameter value. * Set the $mediapool variable as the FullBackupMediaPool parameter value. * Set the $monthlypolicy variable as the FullBackupPolicy parameter value. * Set the $mediapool variable as the IncrementalBackupMediaPool parameter value. * Set the $dailypolicy variable as the IncrementalBackupPolicy parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating GFS Object to Tape Job

|  |  |
| --- | --- |
| This example shows how to create a GFS object to tape job that backs up the Sydney Container Microsoft Azure container.  |  | | --- | | $server = Get-VBRUnstructuredServer -Name "Azure Blob Storage"  $object = New-VBRObjectStorageBackupJobObject -Server $server -Container "Sydney Container"  $mediapool = Get-VBRTapeMediaPool -Name "GFS Media Pool"  $schedule = New-VBRTapeGFSScheduleOptions -MonthlyKind DayOfMonth -MonthlyDayOfMonth 1  Add-VBRObjectToTapeJob -Name "Sydney Container to Tape" -Description "Backing up Sydney Azure Container" -Object $object -GFSMediaPool $mediapool -GFSScheduleOptions $schedule |  Perform the following steps:   1. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [New-VBRObjectStorageBackupJobObject](new-vbrobjectstoragebackupjobobject.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Container parameter value. Save the result to the $object variable. 3. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save the result to the $mediapool variable. 4. Run the [New-VBRTapeGFSScheduleOptions](new-vbrtapegfsscheduleoptions.md) cmdlet. Specify the MonthlyKind and MonthlyDayOfMonth parameter values. Save the result to the $schedule variable. 5. Run the Add-VBRObjectToTapeJob cmdlet. Specify the following settings:  * Specify the Name and the Description parameter values. * Set the $object variable as the Object parameter value. * Set the $mediapool variable as the GFSMediaPool parameter value. * Set the $schedule variable as the GFSScheduleOptions parameter value. |

Related Commands

* [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)
* [New-VBRObjectStorageBackupJobObject](new-vbrobjectstoragebackupjobobject.md)
* [Get-VBRTapeMediaPool](get-vbrtapemediapool.md)
* [New-VBRFileToTapeBackupPolicy](new-vbrfiletotapebackuppolicy.md)
* [New-VBRNotificationOptions](new-vbrnotificationoptions.md)
* [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md)
* [New-VBRTapeGFSScheduleOptions](new-vbrtapegfsscheduleoptions.md)


