---
title: "New-VBRApplicationBackupRepositoryScheduleOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrapplicationbackuprepositoryscheduleoptions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# New-VBRApplicationBackupRepositoryScheduleOptions


Short Description

Creates a snapshot creation schedule for application backup repositories.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRApplicationBackupRepositoryScheduleOptions -Type {Daily | Monthly | Periodically | AfterJob | RunManually} [-DailyOptions <VBRDailyOptions>] [-MonthlyOptions <VBRMonthlyOptions>] [-PeriodicallyOptions <VBRPeriodicallyOptions>] [-ScheduleEnabled <Boolean>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a schedule according to which the application backup repository creates snapshots of the repository volume.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Type | Specifies the type of the schedule:   * Daily * Monthly * Periodically * AfterJob * RunManually   The cmdlet will create the snapshot schedule of this type. | VBRServerScheduleType | True | Named | False |
| DailyOptions | For daily schedule.  Specifies daily schedule settings. The cmdlet will create the snapshot schedule with these settings. | Accepts the [VBRDailyOptions](vbrdailyoptions.md) object. To create this object, run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. | False | Named | False |
| MonthlyOptions | For monthly schedule.  Specifies monthly schedule settings. The cmdlet will create the snapshot schedule with these settings. | Accepts the [VBRMonthlyOptions](vbrmonthlyoptions.md) object. To create this object, run the [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md) cmdlet. | False | Named | False |
| PeriodicallyOptions | For periodical schedule.  Specifies periodical schedule settings. The cmdlet will create the snapshot schedule with these settings. | Accepts the [VBRPeriodicallyOptions](vbrperiodicallyoptions.md) object. To create this object, run the [New-VBRPeriodicallyOptions](new-vbrperiodicallyoptions.md) cmdlet. | False | Named | False |
| ScheduleEnabled | Determines whether the snapshot creation schedule is enabled or not. | Boolean | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the [VBRApplicationBackupRepositoryScheduleOptions](vbrapplicationbackuprepositoryscheduleoptions.md) object that contains the snapshot schedule for a application backup repository.

Examples

Creating Snapshot Schedule for Application Backup Repository

This example shows how to create a new snapshot creation schedule which runs every Friday at 23:00.

|  |
| --- |
| $daily = New-VBRDailyOptions -DayOfWeek Friday -Period 23:00  $schedule = New-VBRApplicationBackupRepositoryScheduleOptions -ScheduleEnabled $true -Type Daily -DailyOptions $daily |

Perform the following steps:

1. Run the [New-VBRDailyOptions](get-vbrapplicationbackuprepository.md) cmdlet. Specify the DayofWeek and Period parameter values. Save the result to the $daily variable.
2. Run the New-VBRApplicationBackupRepositoryScheduleOptions cmdlet. Specify the following settings:

* Set the ScheduleEnabled parameter value to $true.
* Specify the Type parameter value.
* Set the $daily variable as the DailyOptions parameter value.
* Save the result to the $schedule variable to be used with other cmdlets.

Related Commands

* [New-VBRDailyOptions](new-vbrdailyoptions.md)
* [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md)
* [New-VBRPeriodicallyOptions](new-vbrperiodicallyoptions.md)

Page updated 2026-06-04

