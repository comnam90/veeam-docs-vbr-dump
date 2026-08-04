---
title: "New-VBRMacScheduleOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrmacscheduleoptions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# New-VBRMacScheduleOptions


Short Description

Defines the schedule for macOS jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRMacScheduleOptions -Type {Daily | Monthly | Periodically | AfterJob} [-DailyOptions <VBRDailyOptions>] [-MonthlyOptions <VBRMonthlyOptions>] [-PeriodicallyOptions <VBRPeriodicallyOptions>] [-EnableRetry] [-RetryCount<int>] [-RetryTimeout <int>] [-EnableBackupTerminationWindow] [-TerminationWindow <VBRBackupWindowOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRMacScheduleOptions](vbrmacscheduleoptions.md) object. This object defines schedule for macOS jobs.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Type | Specifies the macOS schedule type.   * Daily: use this option to run the job at a specific time daily. * Monthly: use this option to run the job once a month on specific days. * Periodically: use this option to run the job repeatedly throughout a day with a specific time interval. * AfterJob: use this option to create a chain of jobs. Veeam Backup & Replication will start the macOS job after the other backup job. Note: The AfterJob option does not work for backup policy. | VBRServerScheduleType | True | Named | False |
| DailyOptions | For daily schedule.  Specifies daily schedule settings. The cmdlet will create the server schedule with these settings. | Accepts the [VBRDailyOptions](vbrdailyoptions.md) object. To get this object, run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. | False | Named | False |
| MonthlyOptions | For monthly schedule.  Specifies monthly schedule settings. The cmdlet will create the server schedule with these settings. | Accepts the [VBRMonthlyOptions](vbrmonthlyoptions.md) object. To get this object, run the [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md) cmdlet. | False | Named | False |
| PeriodicallyOptions | For periodical run.  Specifies periodical schedule settings. The cmdlet will create the server schedule with these settings. | Accepts the [VBRPeriodicallyOptions](vbrperiodicallyoptions.md) object. To get this object, run the [New-VBRPeriodicallyOptions](new-vbrperiodicallyoptions.md) cmdlet. | False | Named | False |
| EnableRetry | Enables the option to run a macOS job again in case it fails. | SwitchParameter | False | Named | False |
| RetryCount | For the EnableRetry parameter.  Specifies the number of attempts to run the failed macOS backup job.  Default: 3. | Int | False | Named | False |
| RetryTimeout | For the EnableRetry parameter.  Specifies the time interval between retry attempts in minutes.  Default: 30. | Int | False | Named | False |
| EnableBackupTerminationWindow | Enables the option to stop the Veeam Agent backup job if it exceeds the backup window. | SwitchParameter | False | Named | False |
| TerminationWindow | Specifies the time interval within which the backup job must complete. | Accepts the [VBRBackupWindowOptions](vbrbackupwindowoptions.md) object. To create this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRMacScheduleOptions](vbrmacscheduleoptions.md) object that defines schedule for macOS jobs.

Examples

Defining Schedule for MacOS Jobs

This example shows how to define schedule for MacOS jobs. The job will run on Fridays at 7:00 PM. The job is allowed to run only within the backup window from 20:00 to 22:59, Monday to Friday.

|  |
| --- |
| $daily = New-VBRDailyOptions -DayOfWeek Friday -Period 7:00  $window = New-VBRBackupWindowOptions -FromDay Monday -ToDay Friday -FromHour 20 -ToHour 22 -Enabled  $macschedule = New-VBRMacScheduleOptions -Type Daily -DailyOptions $daily -EnableBackupTerminationWindow -TerminationWindow $window |

Perform the following steps:

1. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Specify the DayOfWeek and Period parameter values. Save the result to the $daily variable.
2. Run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. Specify the FromDay, ToDay, FromHour and ToHour parameter values. Provide the Enabled parameter. Save the result to the $window variable.
3. Run the New-VBRMacScheduleOptions cmdlet. Set the Daily value as the Type parameter value. Set the $daily variable as the DailyOptions parameter value. Provide the EnableBackupTerminationWindow parameter. Set the $window variable as the TerminationWindow parameter value. Save the result to the $macschedule variable to be used with other cmdlets.

Related Commands

* [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md)
* [New-VBRDailyOptions](new-vbrdailyoptions.md)

Page updated 2026-06-03

