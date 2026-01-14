---
title: "Set-VBRMacScheduleOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrmacscheduleoptions.html"
last_updated: "5/6/2024"
product_version: "13.0.1.1071"
---

# Set-VBRMacScheduleOptions

In this article

Short Description

Modifies schedule for macOS jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRMacScheduleOptions -Options <VBRMacScheduleOptions> [-Type {Daily | Monthly | Periodically | AfterJob}] [-DailyOptions <VBRDailyOptions>] [-MonthlyOptions <VBRMonthlyOptions>] [-PeriodicallyOptions <VBRPeriodicallyOptions>] [-EnableRetry] [-RetryCount <int>] [-RetryTimeout <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies schedule for macOS jobs, created with Veeam Agent for Oracle Solaris or Veeam Agent for IBM AIX.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies schedule settings for macOS jobs that you want to modify. | Accepts the VBRMacScheduleOptions object. To get this object, run the [New-VBRMacScheduleOptions](new-vbrmacscheduleoptions.md) cmdlet. | True | Named | False |
| Type | Specifies the macOS schedule type.   * Daily: use this option to run the job at a specific time daily. * Monthly: use this option to run the job once a month on specific days. * Periodically: use this option to run the job repeatedly throughout a day with a specific time interval. * AfterJob: use this option to create a chain of jobs. Veeam Backup & Replication will start the macOS job after the other backup job. | VBRServerScheduleType | False | Named | False |
| DailyOptions | For daily schedule.  Specifies daily schedule settings. The cmdlet will create the server schedule with these settings. | Accepts the [VBRDailyOptions](vbrdailyoptions.md) object. To get this object, run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. | False | Named | False |
| MonthlyOptions | For monthly schedule.  Specifies monthly schedule settings. The cmdlet will create the server schedule with these settings. | Accepts the [VBRMonthlyOptions](vbrmonthlyoptions.md) object. To get this object, run the [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md) cmdlet. | False | Named | False |
| PeriodicallyOptions | For periodical run.  Specifies periodical schedule settings. The cmdlet will create the server schedule with these settings. | Accepts the [VBRPeriodicallyOptions](vbrperiodicallyoptions.md) object. To get this object, run the [New-VBRPeriodicallyOptions](new-vbrperiodicallyoptions.md) cmdlet. | False | Named | False |
| EnableRetry | Enables the option to run a macOS job again in case it fails. | SwitchParameter | False | Named | False |
| RetryCount | For the EnableRetry parameter.  Specifies the number of attempts to run the failed macOS backup job.  Default: 3. | Int | False | Named | False |
| RetryTimeout | For the EnableRetry parameter.  Specifies the time interval between retry attempts in minutes.  Default: 30. | Int | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRMacScheduleOptions object that defines schedule for macOS jobs.

Examples

Defining Schedule for MacOS Jobs

This example shows how to modify schedule for macOS jobs. The job schedule will be set to run on Wednesday instead of Fridays.

|  |
| --- |
| $daily = New-VBRDailyOptions -DayOfWeek Friday -Period 7:00  $macschedule = New-VBRMacScheduleOptions -Type Daily -DailyOptions $daily  $newdaily = New-VBRDailyOptions -DayOfWeek Wednesday -Period 7:00  Set-VBRMacScheduleOptions -Options $macschedule -DailyOptions $newdaily |

Perform the following steps:

1. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Specify the DayOfWeek and Period parameter values. Save the result to the $daily variable.
2. Run the [New-VBRMacScheduleOptions](new-vbrmacscheduleoptions.md) cmdlet. Set the Daily option for the Type parameter. Set the $daily variable as the DailyOptions parameter value. Save the result to the $macschedule variable.
3. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Specify the DayOfWeek and Period parameter values. Save the result to the $newdaily variable.
4. Run the Set-VBRMacScheduleOptions cmdlet. Set the $macschedule variable as the Options parameter value. Set the $newdaily variable as the DailyOptions parameter value.

Related Commands

* [New-VBRDailyOptions](new-vbrdailyoptions.md)
* [New-VBRMacScheduleOptions](new-vbrmacscheduleoptions.md)
* [New-VBRDailyOptions](new-vbrdailyoptions.md)

Page updated 5/6/2024

Page content applies to build 13.0.1.1071
