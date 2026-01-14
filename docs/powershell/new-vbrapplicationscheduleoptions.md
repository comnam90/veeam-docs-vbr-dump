---
title: "New-VBRApplicationScheduleOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrapplicationscheduleoptions.html"
last_updated: "3/8/2024"
product_version: "13.0.1.1071"
---

# New-VBRApplicationScheduleOptions

In this article

Short Description

Creates the schedule for application backup policies.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRApplicationScheduleOptions -Type {Daily | Monthly | Periodically | AfterJob} [-DailyOptions <VBRDailyOptions>] [-MonthlyOptions <VBRMonthlyOptions>] [-PeriodicallyOptions <VBRPeriodicallyOptions>] [-Job <CBackupJob>] [-EnableRetry] [-RetryCount <int>] [-RetryTimeout <int>] [-EnableBackupTerminationWindow] [-TerminationWindow <VBRBackupWindowOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRApplicationScheduleOptions object that contains schedule settings for application backup policies.

You can use this cmdlet to create a schedule for application backup policies for the following Veeam Plug-Ins managed by Veeam Backup & Replication:

* Veeam Plug-In for Oracle RMAN
* Veeam Plug-In for SAP HANA
* Veeam Plug-In for SAP on Oracle

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Type | Specifies the backup job schedule type.   * Daily: use this option to run the job at a specific time daily. * Monthly: use this option to run the job once a month on specific days. * Periodically: use this option to run the job repeatedly throughout a day with a specific time interval. * AfterJob: use this option to create a chain of jobs. Veeam Backup & Replication will start the Veeam Agent backup job after the other backup job. | VBRApplicationScheduleType | True | Named | False |
| DailyOptions | For daily schedule.  Specifies daily schedule settings. The cmdlet will create the server schedule with these settings. | Accepts the VBRDailyOptions object. To get this object, run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. | False | Named | False |
| MonthlyOptions | For monthly schedule.  Specifies monthly schedule settings. The cmdlet will create the server schedule with these settings. | Accepts the VBRMonthlyOptions object. To get this object, run the [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md) cmdlet. | False | Named | False |
| PeriodicallyOptions | For periodical run.  Specifies periodical schedule settings. The cmdlet will create the server schedule with these settings. | Accepts the VBRPeriodicallyOptions object. To get this object, run the [New-VBRPeriodicallyOptions](new-vbrperiodicallyoptions.md) cmdlet. | False | Named | False |
| Job | For running after a job.  Specifies the name of the backup job after which Veeam Backup & Replication will run application backup policies. The cmdlet will create the schedule with these settings. | Accepts the CBackupJob object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | False | Named | False |
| EnableRetry | Enables the option to run the Veeam Agent backup job again in case it fails. | SwitchParameter | False | Named | False |
| RetryCount | For the EnableRetry parameter.  Specifies the number of attempts to run the failed Veeam Agent backup job.  Permitted values: 1 to 999. | Int | False | Named | False |
| RetryTimeout | For the EnableRetry parameter.  Specifies the time interval between retry attempts in minutes.  Permitted values: 1 to 999. | Int | False | Named | False |
| EnableBackupTerminationWindow | Enables the option to stop the Veeam Agent backup job if it exceeds the backup window. | SwitchParameter | False | Named | False |
| TerminationWindow | Specifies the time interval within which the backup job must complete. The cmdlet will create the Veeam Agent backup job with these settings. | Accepts the VBRBackupWindowOptions object. To get this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRApplicationScheduleOptions object that defines schedule settings for application backup policies.

Examples

Creating Schedule for Application Backup Policy

This example shows how to create the schedule for an application backup policy. The job will run on Fridays at 7:00 PM.

|  |
| --- |
| $daily = New-VBRDailyOptions -DayOfWeek Friday -Period 7:00  New-VBRApplicationScheduleOptions -Type Daily -DailyOptions $daily |

Perform the following steps:

1. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Specify the DayOfWeek and Period parameter values. Save the result to the $daily variable.
2. Run the New-VBRApplicationScheduleOptions cmdlet. Set the Daily option for the Type parameter. Set the $daily variable as the DailyOptions parameter value.

Related Commands

[New-VBRDailyOptions](new-vbrdailyoptions.md)

Page updated 3/8/2024

Page content applies to build 13.0.1.1071
