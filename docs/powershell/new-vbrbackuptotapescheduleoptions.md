---
title: "New-VBRBackupToTapeScheduleOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrbackuptotapescheduleoptions.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# New-VBRBackupToTapeScheduleOptions

In this article

Short Description

Creates schedule settings for backup to tape job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRBackupToTapeScheduleOptions [-Type <VBRBackupToTapePolicyType>] [-DailyOptions <VBRDailyOptions>] [-MonthlyOptions <VBRMonthlyOptions>] [-BackupWindowOptions <VBRBackupWindowOptions>] [-Job <VBRJob>] [-Enabled]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRBackupToTapeScheduleOptions](vbrbackuptotapescheduleoptions.md) object. This object contains schedule settings for backup to tape job and is used further to apply these settings to an existing backup to tape job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Type | Specifies the job schedule type:   * AfterJob: the tape job will wait for the source backup job to complete.  * AfterNewBackup: the tape job will periodically check the source jobs for new backups and archive new backups to tape. * Daily: the tape job will run on selected days. Use the DailyOptions parameter to set the days. * Monthly: the tape job will run on selected months. Use the MonthlyOptions parameter to set the months.   Default: Daily. | [VBRBackupToTapePolicyType](enums.md#VBRBackupToTapePolicyType) | False | Named | False |
| DailyOptions | Used to set days for the Type parameter (Daily option).  Default:   * Type: SelectedDays. * Period: 18:00. * DayOfWeek: Saturday. | Accepts the [VBRDailyOptions](vbrdailyoptions.md) object. To create this object, run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. | False | Named | False |
| MonthlyOptions | Used to set months for the Type parameter (Monthly option).  Default:   * Period: 22:00. * DayNumberInMonth: Fourth. * DayOfWeek: Saturday.  * Months: January, February, March, April, May, June, July, August, September, October, November, December. | Accepts the [VBRMonthlyOptions](vbrmonthlyoptions.md) object. To create this object, run the [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md) cmdlet. | False | Named | False |
| BackupWindowOptions | Specifies backup windows: the tape job will run within the specified time interval.  Default:   * From Sunday to Saturday. * From 00:00 to 23:00. * Enabled: True. | Accepts the VBRBackupWindowOptions object. To create this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |
| Job | Specifies the source backup job after which the tape job must run. | Accepts the CBackupJob or the [VBRJob](vbrjob.md) objects. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | False | Named | False |
| Enabled | Defines if this schedule is enabled.  Default: False. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRBackupToTapeScheduleOptions](vbrbackuptotapescheduleoptions.md)

Examples

Creating Tape Job Schedule

This example shows how to create a tape job schedule with the following settings:

* The job runs every Friday.
* The job starts at 23:00.

|  |
| --- |
| $dailyoptions = New-VBRDailyOptions -DayOfWeek Friday -Period 23:00  $scheduleoptions = New-VBRBackupToTapeScheduleOptions -DailyOptions $dailyoptions -Enabled |

Perform the following steps:

1. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Set Friday as the DayOfWeek parameter value and 23:00 as the Period parameter value. Save the result to the $dailyoptions variable.
2. Run the [New-VBRBackupToTapeScheduleOptions](new-vbrbackuptotapescheduleoptions.md) cmdlet. Set the $dailyoptions variable as the DailyOptions parameter value. Provide the Enabled parameter. Save the schedule to the $scheduleoptions variable for future use.

Related Commands

* [New-VBRDailyOptions](new-vbrdailyoptions.md)
* [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md)
* [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md)
* [Get-VBRJob](get-vbrjob.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
