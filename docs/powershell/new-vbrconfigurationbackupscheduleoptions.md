---
title: "New-VBRConfigurationBackupScheduleOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrconfigurationbackupscheduleoptions.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# New-VBRConfigurationBackupScheduleOptions

In this article

Short Description

Creates a new [VBRConfigurationBackupScheduleOptions](vbrconfigurationbackupscheduleoptions.md) object.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRConfigurationBackupScheduleOptions [-Enable] [-Type <VBRConfigurationBackupScheduleType> {Daily | Monthly}] [-DailyOptions <VBRDailyOptions>] [-MonthlyOptions <VBRMonthlyOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new [VBRConfigurationBackupScheduleOptions](vbrconfigurationbackupscheduleoptions.md) object. This object contains schedule settings for configuration backup job. It is used then in the [Set-VBRConfigurationBackupJob](set-vbrconfigurationbackupjob.md) cmdlet.

If you run this cmdlet without parameters, it will create an object with default settings.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Enable | Defines that the job will run automatically on schedule.  If set to False, you will need to run the job manually.  Default: True.  Note: To disable the configuration job schedule, specify the $false value for the Enable parameter. | SwitchParameter | False | Named | False |
| Type | Specifies the type of the schedule:   * Daily * Monthly   Default: Daily. | [VBRConfigurationBackupScheduleType](enums.md#VBRConfigurationBackupScheduleType) | False | Named | False |
| DailyOptions | For daily schedule.  Specifies the daily schedule options.  Default: 10:00, everyday. | Accepts the [VBRDailyOptions](vbrdailyoptions.md) object. To get this object, run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. | False | Named | False |
| MonthlyOptions | For monthly schedule.  Specifies the monthly schedule options.  Default: 22:00, Fourth Saturday, all months. | Accepts the [VBRMonthlyOptions](vbrmonthlyoptions.md) object. To get this object, run the [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRConfigurationBackupScheduleOptions](vbrconfigurationbackupscheduleoptions.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Object with Default Configuration Job Schedule Settings

|  |  |
| --- | --- |
| This command creates an object with default configuration job schedule settings. The object is saved to the $defaultschedule variable.  |  | | --- | | $defaultschedule = New-VBRConfigurationBackupScheduleOptions | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Setting Daily Schedule for Configuration Backup Job

|  |  |
| --- | --- |
| This example shows how to set daily schedule for the configuration backup job. The job will run on 5 AM on Saturdays.  |  | | --- | | $daily = New-VBRDailyOptions -Period "05:00" -DayOfWeek Saturday  $dailyschedule = New-VBRConfigurationBackupScheduleOptions -Type Daily -DailyOptions $daily |  Perform the following steps:   1. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Specify the DayOfWeek and the Period parameter values. Save the result to the $daily variable. 2. Run the New-VBRConfigurationBackupScheduleOptions cmdlet. Set the Daily option for the Type parameter. Set the $daily variable as the DailyOptions parameter value. Save the result to the $dailyschedule variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Setting Monthly Schedule for Configuration Backup Job

|  |  |
| --- | --- |
| This example shows how to set monthly schedule for the configuration backup job. The job will run on 00:00 the first Friday of each month.  |  | | --- | | $monthly = New-VBRMonthlyOptions -Period "00:00" -DayOfWeek Friday -DayNumberInMonth First  $monthlyschedule = New-VBRConfigurationBackupScheduleOptions -Type Monthly -MonthlyOptions $monthly |  Perform the following steps:   1. Run the [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md) cmdlet. Specify the Period, the DayOfWeek and the DayNumberInMonth parameter values. Save the result to the $monthly variable. 2. Run the New-VBRConfigurationBackupScheduleOptions cmdlet. Set the Monthly option for the Type parameter. Set the $monthly variable as the MonthlyOptions parameter value. Save the result to the $monthlyschedule variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Disabling Configuration Job Schedule

|  |  |
| --- | --- |
| This command disables the configuration job schedule. The object is saved to the $disableschedule variable.  |  | | --- | | $disableschedule = New-VBRConfigurationBackupScheduleOptions -Enable:$false | |

Related Commands

* [New-VBRDailyOptions](new-vbrdailyoptions.md)
* [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md)

Page updated 5/17/2024

Page content applies to build 13.0.1.1071
