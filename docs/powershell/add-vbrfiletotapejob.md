---
title: "Add-VBRFileToTapeJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrfiletotapejob.html"
last_updated: "12/19/2025"
product_version: "13.0.1.1071"
---

# Add-VBRFileToTapeJob

In this article

Short Description

Creates a file to tape job or a GFS file to tape job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Create a file to tape job.

|  |
| --- |
| Add-VBRFileToTapeJob -Name <string> -FullBackupMediaPool <VBRTapeMediaPool> [-Description <string>] [-EjectCurrentMedium] [-ExportCurrentMediaSet] -FullBackupMediaPool <VBRTapeMediaPool> [-IncrementalBackupMediaPool <VBRTapeMediaPool>] [-ExportDays<DayOfWeek[]>] [-FullBackupPolicy <VBRFileToTapeBackupPolicy>] [-IncrementalBackupPolicy <VBRFileToTapeBackupPolicy>] [-Object <VBRFileToTapeObject[]>] [-NdmpObject <VBRNDMPVolume[]>] [-UseVSS] [-UseHardwareCompression] [-NotificationOptions <VBRNotificationOptions>] [-JobScriptOptions <VBRJobScriptOptions>] [-Force] [-EnableParallelDrivesUsage] [-LimitTapeDrives <int>] [-EnableFileAclChangeTracking]  [<CommonParameters>] |

* Create a GFS file to tape job.

|  |
| --- |
| Add-VBRFileToTapeJob -Name <string> -GFSMediaPool <VBRTapeGFSMediaPool> [-Description <string>] [-EjectCurrentMedium] [-ExportCurrentMediaSet] [-GFSMediaSetsToExport {Daily | Weekly | Monthly | Quarterly | Yearly}] [-FullBackupPolicy <VBRFileToTapeBackupPolicy>] [-IncrementalBackupPolicy <VBRFileToTapeBackupPolicy>] [-Object <VBRFileToTapeObject[]>] [-NdmpObject <VBRNDMPVolume[]>] [-UseVSS] [-UseHardwareCompression] [-GFSScheduleOptions <VBRTapeGFSScheduleOptions>] [-NotificationOptions <VBRNotificationOptions>] [-JobScriptOptions <VBRJobScriptOptions>] [-Force] [-EnableParallelDrivesUsage] [-LimitTapeDrives <int>] [-EnableFileAclChangeTracking]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new file to tape job or a GFS file to tape job. You can target the job to a simple or a GFS media pool.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name you want to assign to the file to tape job. | String | True | Named | False |
| Description | Specifies the description of the file to tape job. | String | False | Named | False |
| EjectCurrentMedium | Defines that the tapes will be automatically ejected from drive after the job finishes.  The ejected tape is moved to a standard library slot. | SwitchParameter | False | Named | False |
| ExportCurrentMediaSet | For non-GFS file to tape jobs.  Defines that the tapes belonging to the media set will be automatically placed to Import/Export (Mail) slot for further export. Use the ExportDays parameter to set days on which you want to export tapes.  If you use this parameter, but do not set the ExportDays parameter, the tapes will be exported every day. | SwitchParameter | False | Named | False |
| FullBackupMediaPool | For non-GFS file to tape jobs.  Specifies the media pool where you want to store full backups produced by this tape job. | Accepts the [VBRTapeMediaPool](vbrtapemediapool.md) obejct, GUID or string. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | True | Named | False |
| IncrementalBackupMediaPool | For non-GFS file to tape jobs.  Used to set media pool for the ProcessIncrementalBackup parameter.  Specifies the media pool where you want to store incremental backups produced by this tape job.  If you do not specify a media pool, incremental backups will be stored to the media pool the you set for full backups. | Accepts the [VBRTapeMediaPool](vbrtapemediapool.md) obejct, GUID or string. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | False | Named | False |
| GFSMediaPool | For GFS file to tape jobs.  Specifies the target GFS media pool. | Accepts the [VBRTapeGFSMediaPool](vbrtapegfsmediapool.md) object, GUID or string. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | True | Named | False |
| ExportDays | Used to set days for exporting tapes for the ExportCurrentMediaSet parameter.  Specifies days on which the tapes written by this tape job will be automatically exported: Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday. | DayOfWeek[] | False | Named | False |
| GFSMediaSetsToExport | For GFS file to tape jobs.  Specifies GFS media sets for which the tapes will be automatically exported once the tape job is finished:   * Daily * Weekly * Monthly * Quarterly * Yearly | VBRGFSMediaSetTypeToExport[] | False | Named | False |
| FullBackupPolicy | Specifies virtualized synthetic full backup for tape settings.  Default:   * Type: Daily * DailyOptions: Type: SelectedDays, Period: 18:00, DayOfWeek: Saturday * MonthlyOptions: Period: 22:00, DayNumberInMonth: Fourth, DayOfWeek: Saturday, Months: January, February, March, April, May, June, July, August, September, October, November, December * Enabled: False | Accepts the [VBRFileToTapeBackupPolicy](vbrfiletotapebackuppolicy.md) object. To create this object, run the [New-VBRFileToTapeBackupPolicy](new-vbrfiletotapebackuppolicy.md) cmdlet. | False | Named | False |
| IncrementalBackupPolicy | Specifies incremental backup settings.  Default:   * Type: Daily. * DailyOptions: Type: SelectedDays, Period: 18:00, DayOfWeek: Saturday. * MonthlyOptions: Period: 22:00, DayNumberInMonth: Fourth, DayOfWeek: Saturday, Months: January, February, March, April, May, June, July, August, September, October, November, December. * Enabled: False. | Accepts the [VBRFileToTapeBackupPolicy](vbrfiletotapebackuppolicy.md) object. To create this object, run the [New-VBRFileToTapeBackupPolicy](new-vbrfiletotapebackuppolicy.md) cmdlet. | False | Named | False |
| Object | Specifies the array of file to tape job sources. | Accepts the [VBRFileToTapeJob](vbrfiletotapejob.md) object. To create this object, run the [New-VBRFileToTapeObject](new-vbrfiletotapeobject.md) cmdlet. | False | Named | False |
| NdmpObject | Specifies the array of NDMP server volumes. | Accepts the VBRNDMPVolume[] object. Run the [Get-VBRNDMPVolume](get-vbrndmpvolume.md) cmdlet to get this object. | False | Named | False |
| UseVSS | Defines that the VSS (Microsoft Volume Shadow Copy) must be used.  Default: True.  Note: To disable this option, set the parameter value to $false. That is, parameter\_name:$false. | SwitchParameter | False | Named | False |
| UseHardwareCompression | Defines that tape library must perform hardware compression for archives. Do not use this option for archiving Veeam backups or other already compressed files. | SwitchParameter | False | Named | False |
| GFSScheduleOptions | For GFS file to tape jobs.  Specifies the schedule settings for the GFS media pool. | Accepts the [VBRTapeGFSScheduleOptions](vbrtapegfsscheduleoptions.md) object. To create this object, run the [New-VBRTapeGFSScheduleOptions](new-vbrtapegfsscheduleoptions.md) cmdlet. | False | Named | False |
| NotificationOptions | Specifies the email notification options. | Accepts the [VBRNotificationOptions](vbrnotificationoptions.md) object. To create this object, run the [New-VBRNotificationOptions](new-vbrnotificationoptions.md) cmdlet. | False | Named | False |
| JobScriptOptions | Specifies the scripting options. | Accepts the [VBRJobScriptOptions](vbrjobscriptoptions.md) object. To create this object, run the [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will create a job even if the geographic location of the repositories where VM backups reside and the target media pool location do not match. | SwitchParameter | False | Named | False |
| EnableParallelDrivesUsage | Enables parallel processing of media pools.  Default: False. | SwitchParameter | False | Named | False |
| LimitTapeDrives | Defines that the cmdlet will limit the number of drives to use for processing this tape job.  Default: 2 drives. | Int32 | False | Named | False |
| EnableFileAclChangeTracking | Enables backup of permissions and attributes for files.  Default: False. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRFileToTapeJob](vbrfiletotapejob.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating File to Tape Job

|  |  |
| --- | --- |
| This example shows how to create a file to tape job that backs up the Payroll Reports folder. The job runs once a month and creates only full backups.  |  | | --- | | $server = Get-VBRServer -Name "fileserver08.tech.local"  $creds = Get-VBRCredentials -Description "Fileserver08 Adminisrator"  $object = New-VBRFileToTapeObject -Server $server -Path "D:\Summary Reports\Payroll Reports" -Credentials $creds  $mediapool = Get-VBRTapeMediaPool -Name "File Backup Media Pool"  $monthlyoptions = New-VBRMonthlyOptions -DayNumberInMonth Last -DayOfWeek Sunday -Period 22:00  $policy = New-VBRFileToTapeBackupPolicy -Type Monthly -MonthlyOptions $monthlyoptions -Enabled  Add-VBRFileToTapeJob -Name "Payroll Reports to Tape" -Description "Finance reports: summary reports" -Object $object -FullBackupMediaPool $mediapool -FullBackupPolicy $policy |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet to get the server where the files are located. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Description parameter value. Save the result to the $creds variable. 3. Run the [New-VBRFileToTapeObject](new-vbrfiletotapeobject.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Path parameter value. Set the $creds variable as the Credentials parameter value. Save the result to the $object variable. 4. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save the result to the $mediapool variable. 5. Run the [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md) cmdlet. Specify the DayNumberInMonth, DayOfWeek and Period parameter values. Save the result to the $monthlyoptions variable. 6. Run the [New-VBRFileToTapeBackupPolicy](new-vbrfiletotapebackuppolicy.md) cmdlet. Set the Monthly option for the Type parameter. Set the $monthlyoptions variable as the MonthlyOptions parameter value. Provide the Enabled parameter. Save the result to the $policy variable. 7. Run the Add-VBRFileToTapeJob cmdlet. Specify the following settings:  * Specify the Name and the Description parameter values. * Set the $object variable as the Object parameter value. * Set the $mediapool variable as the FullBackupMediaPool parameter value. * Set the $policy variable as the FullBackupPolicy parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating GFS File to Tape Job

|  |  |
| --- | --- |
| This example shows how to create a GFS file to tape job that backs up the Payroll Reports folder.  |  | | --- | | $server = Get-VBRServer -Name "fileserver08.tech.local"  $creds = Get-VBRCredentials -Description "Fileserver08 Adminisrator"  $object = New-VBRFileToTapeObject -Server $server -Path "D:\Summary Reports\Payroll Reports" -Credentials $creds  $mediapool = Get-VBRTapeMediaPool -Name "GFS Media Pool"  $schedule = New-VBRTapeGFSScheduleOptions -MonthlyKind DayOfMonth -MonthlyDayOfMonth 1  Add-VBRFileToTapeJob -Name "Payroll Reports to Tape" -Description "Finance reports: summary reports" -Object $object -GFSMediaPool $mediapool -GFSScheduleOptions $schedule -GFSMediaSetsToExport Yearly |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet to get the server where the files are located. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRCredentials](get-vbrcredentials.md) cmdlet. Specify the Description parameter value. Save the result to the $creds variable. 3. Run the [New-VBRFileToTapeObject](new-vbrfiletotapeobject.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Path parameter value. Set the $creds variable as the Credentials parameter value. Save the result to the $object variable. 4. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save the result to the $mediapool variable. 5. Run the [New-VBRTapeGFSScheduleOptions](new-vbrtapegfsscheduleoptions.md) cmdlet. Specify the MonthlyKind and MonthlyDayOfMonth parameter values. Save the result to the $schedule variable. 6. the Add-VBRFileToTapeJob cmdlet. Specify the following settings:  * Specify the Name and the Description parameter values. * Set the $object variable as the Object parameter value. * Set the $mediapool variable as the GFSMediaPool parameter value. * Set the $schedule variable as the GFSScheduleOptions parameter value. * Set the Yearly value as the GFSMediaSetsToExport parameter value. |

Related Commands

* [Get-VBRTapeMediaPool](get-vbrtapemediapool.md)
* [New-VBRFileToTapeBackupPolicy](new-vbrfiletotapebackuppolicy.md)
* [New-VBRFileToTapeObject](new-vbrfiletotapeobject.md)
* [New-VBRTapeGFSScheduleOptions](new-vbrtapegfsscheduleoptions.md)
* [New-VBRNotificationOptions](new-vbrnotificationoptions.md)
* [New-VBRJobScriptOptions](new-vbrjobscriptoptions.md)

Page updated 12/19/2025

Page content applies to build 13.0.1.1071
