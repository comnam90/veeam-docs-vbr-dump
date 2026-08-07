---
title: "New-VBRLinuxScheduleOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrlinuxscheduleoptions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# New-VBRLinuxScheduleOptions


Short Description

Creates the schedule for backup policies for Linux computers.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRLinuxScheduleOptions -Type <VBRServerScheduleType> {Daily | Monthly | Periodically | AfterJob} [-DailyOptions <VBRDailyOptions>] [-MonthlyOptions <VBRMonthlyOptions>] [-PeriodicallyOptions <VBRPeriodicallyOptions>] [-EnableRetry] [-RetryCount <int>] [-RetryTimeout <int>] [-EnableBackupTerminationWindow] [-TerminationWindow <VBRBackupWindowOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the [VBRLinuxScheduleOptions](vbrlinuxscheduleoptions.md) object. This object contains schedule settings for a backup policy that the Veeam Agent backup job applies to Linux computers.

|  |
| --- |
| ![New-VBRLinuxScheduleOptions](images/icon_note.webp) Note: |
| For Veeam Agent jobs that back up Linux servers use the [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) cmdlet. |

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Type | Specifies the Veeam Agent backup job schedule type.   * Daily: use this option to run the job at a specific time daily. * Monthly: use this option to run the job once a month on specific days. * Periodically: use this option to run the job repeatedly throughout a day with a specific time interval. | VBRServerScheduleType | True | Named | False |
| DailyOptions | For daily schedule.  Specifies daily schedule settings. The cmdlet will create the server schedule with these settings. | Accepts the [VBRDailyOptions](vbrdailyoptions.md) object. To get this object, run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. | False | Named | False |
| MonthlyOptions | For monthly schedule.  Specifies monthly schedule settings. The cmdlet will create the server schedule with these settings. | Accepts the [VBRMonthlyOptions](vbrmonthlyoptions.md) object. To get this object, run the [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md) cmdlet. | False | Named | False |
| PeriodicallyOptions | For periodical schedule.  Specifies periodically schedule settings. The cmdlet will create the server schedule with these settings. | Accepts the [VBRPeriodicallyOptions](vbrperiodicallyoptions.md) object. To get this object, run the [New-VBRPeriodicallyOptions](new-vbrperiodicallyoptions.md) cmdlet. | False | Named | False |
| EnableRetry | Enables the option for the Veeam Agent for Linux to try to run the Veeam Agent backup job in case it fails. | SwitchParameter | False | Named | False |
| RetryCount | For the EnableRetry parameter.  Specifies the number of attempts to run the failed Veeam Agent backup job.  Default: 3. | Int | False | Named | False |
| RetryTimeout | For the EnableRetry parameter.  Specifies a timeout interval between retry attempts in minutes.  Default: 30. | Int | False | Named | False |
| EnableBackupTerminationWindow | Enables the option to stop the Veeam Agent backup job if it exceeds the backup window. | SwitchParameter | False | Named | False |
| TerminationWindow | Specifies the time interval within which the backup job must complete. | Accepts the [VBRBackupWindowOptions](vbrbackupwindowoptions.md) object. To create this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the [VBRLinuxScheduleOptions](vbrlinuxscheduleoptions.md) object that contains the schedule for the backup policies for Linux computers.

Examples

Creating Monthly Schedule for Veeam Agent Job for Linux Computers

This example shows how to create a monthly schedule for a Veeam Agent job that backs up Linux computers. The job will run monthly at 3:00 AM on the first Sunday. The job is allowed to run only within the backup window from 20:00 to 22:59, Monday to Friday.

|  |
| --- |
| $monthly = New-VBRMonthlyOptions -Period 3:00 -DayNumberInMonth OnDay -DayOfMonth 20  $window = New-VBRBackupWindowOptions -FromDay Monday -ToDay Friday -FromHour 20 -ToHour 22 -Enabled  New-VBRLinuxScheduleOptions -Type Monthly -EnableRetry -RetryCount 7 -RetryTimeout 15 -MonthlyOptions $monthly -EnableBackupTerminationWindow -TerminationWindow $window |

Perform the following steps:

1. Run the [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md) cmdlet. Specify the Period, DayNumberInMonth and DayOfMonth parameter values. Save the result to the $monthly variable.
2. Run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. Specify the FromDay, ToDay, FromHour and ToHour parameter values. Provide the Enabled parameter. Save the result to the $window variable.
3. Run the New-VBRLinuxScheduleOptions cmdlet. Specify the following settings:

* Set the Monthly option for the Type parameter.
* Provide the EnableRetry parameter.
* Specify the RetryCount parameter value.
* Specify the RetryTimeout parameter value.
* Set the $monthly variable as the MonthlyOptions parameter value.
* Provide the EnableBackupTerminationWindow parameter.
* Set the $window variable as the TerminationWindow parameter value.

Related Commands

* [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md)
* [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md)

Page updated 2026-06-03

