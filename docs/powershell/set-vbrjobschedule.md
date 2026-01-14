---
title: "Set-VBRJobSchedule"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrjobschedule.html"
last_updated: "8/8/2024"
product_version: "13.0.1.1071"
---

# Set-VBRJobSchedule

In this article

Short Description

Modifies job schedule.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Schedule a job to run daily on specific time, on specific days of week.

|  |
| --- |
| Set-VBRJobSchedule [-At <datetime>] [-Daily] [-DailyKind {Everyday | WeekDays | SelectedDays}] [-Days {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-EnableBackupTerminationWindow] -Job <CBackupJob> [-TerminationWindow <VBRBackupWindowOptions>]  [<CommonParameters>] |

* Schedule a job to run monthly on specific time, on specific days of month, on specific months.

|  |
| --- |
| Set-VBRJobSchedule [-At <datetime>] [-DayOfMonth <string>] [-Days {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-EnableBackupTerminationWindow] -Job <CBackupJob> [-Monthly] [-Months {January | February | March | April | May | June | July | August | September | October | November | December}] [-NumberInMonth {First | Second | Third | Fourth | Last | OnDay}] [-TerminationWindow <VBRBackupWindowOptions>]  [<CommonParameters>] |

* Schedule a job to run periodically within specified period of time or continuously.

|  |
| --- |
| Set-VBRJobSchedule [-EnableBackupTerminationWindow] [-FullPeriod <Int32>] -Job <CBackupJob> [-PeriodicallyKind {Hours | Minutes | Continuously}] [-PeriodicallyOffset <int32>] [-PeriodicallySchedule <VBRBackupWindowOptions>] [-Periodicaly] [-TerminationWindow <VBRBackupWindowOptions>]  [<CommonParameters>] |

* Schedule a job to run after a certain job you specify.

|  |
| --- |
| Set-VBRJobSchedule [-After] [-AfterJob <CBackupJob>] [-EnableBackupTerminationWindow] -Job <CBackupJob> [-TerminationWindow <VBRBackupWindowOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies schedule settings of a selected job.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameters values with new values. The parameters that you omit will remain unchanged. |

|  |
| --- |
| Important |
| The Periodicaly parameter has a typo in spelling. In scripts, enter parameters as specified in command syntax. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the job you want to edit. | Accepts the CBackupJob object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByProperty Name, ByValue) |
| Daily | For daily schedule.  Defines that the job runs daily. | SwitchParameter | False | Named | False |
| At | For daily schedule.  Specifies the job start time.  Default: 10:00. | DateTime | False | Named | False |
| DailyKind | For daily schedule.  Specifies the days to run the job:   * Everyday: the job will run everyday.  * Weekdays: the job will run Monday through Friday.  * SelectedDays: the job will run on specific days (for example, Saturdays). Use the Days parameter to set the days. | DailyKinds | False | Named | False |
| Days | For daily schedule.  Specifies the days of week when the job will run. | DayOfWeek[] | False | Named | False |
| EnableBackupTerminationWindow | Defines that the Veeam Backup & Replication will stop the Veeam Agent backup job if it exceeds the backup window. | SwitchParameter | False | Named | False |
| TerminationWindow | Specifies the time interval within which the backup job must complete. The cmdlet will create the Veeam Agent backup job with these settings. | Accepts the VBRBackupWindowOptions object. To create this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |
| Monthly | For monthly schedule.  Defines that the job runs once a month. | SwitchParameter | False | Named | False |
| At | For monthly schedule.  Specifies the job start time.  Default: 10:00. | DateTime | False | Named | False |
| NumberInMonth | For monthly schedule.  Specifies the number of day in month (for example, Saturday):   * First: the job will run on the first (Saturday) of selected months. * Second: the job will run on the second (Saturday) of selected months. * Third: the job will run on the third (Saturday) of selected months. * Fourth: the job will run on the fourth (Saturday) of selected months. * Last: the job will run on the last (Saturday) of selected months. * OnDay: the job will run on selected day of month. Use the DayOfMonth parameter to specify the day of month. | EDayNumberInMonth | False | Named | False |
| DayOfMonth | For monthly schedule with the OnDay option.  Specifies the day in month: 1-31, Last. | String | False | Named | False |
| Days | For monthly schedule.  Specifies the day of week for the NumberInMonth parameter. | DayOfWeek[] | False | Named | False |
| Months | For monthly schedule.  Specifies the months when the job will run:   * January * February * March * April * May * June * July * August * September * October * November * December | EMonth[] | False | Named | False |
| Periodicaly | Note: This parameter has a typo in spelling. In scripts, enter parameters as specified in command syntax.  For periodical run.  Defines that the job runs periodically (for example, every 6 hours).  Use the FullPeriod and PeriodicallyKind parameters to set the periodical schedule.  Use the PeriodicallySchedule parameter to set backup window. | SwitchParameter | False | Named | False |
| FullPeriod | For periodical run.  Specifies the number of hours or minutes for the PeriodicallyKind parameter. | Int32 | False | Named | False |
| PeriodicallyKind | For periodical run.  Specifies the periodically schedule type:   * Hours: the job will run periodically in specifies number of hours (for example, every 6 hours). * Minutes: the job will run periodically in specified number of minutes (for example, every 30 minutes. * Continuously: the job will start right after it finished. | VBRPeriodicallyKinds | False | Named | False |
| PeriodicallySchedule | For periodical run.  Specifies the backup window. | Accepts the VBRBackupWindowOptions object. To create this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |
| PeriodicallyOffset | For periodical run.  Used to set the exact time when the backup window starts.  Specifies the number of minutes (1-59). The job will start at the hour set in the backup window plus the indicated period (for example, at 8:30). | Int32 | False | Named | False |
| After | For running after a job.  Defines that the job will start after another job.  Use the AfterJob parameter to set the primary job. | SwitchParameter | False | Named | False |
| AfterJob | For running after a job.  Specifies the job after which you want to run this job. | Accepts the CBackupJob object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Scheduling Daily Backup Job

|  |  |
| --- | --- |
| This example shows how to schedule the Backup Job 01 job to run daily at 23:00 on weekdays.  |  | | --- | | $job = Get-VBRJob -Name "Backup Job 01"  Set-VBRJobSchedule -Job $job -Daily -At "23:00" -DailyKind Weekdays |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Set-VBRJobSchedule cmdlet. Specify the following settings:  * Set the $job variable as the Job parameter value. * Provide the Daily parameter. * Specify the At parameter value. * Specify the DailyKind parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Scheduling Monthly Replication Jobs

|  |  |
| --- | --- |
| This example shows how to schedule all replication jobs to run monthly every last Saturday at 12:00 in February, May, August and December.  |  | | --- | | $job = Get-VBRJob -Name Replica\*  Set-VBRJobSchedule -Job $job -Monthly -At "12:00" -NumberInMonth Last -Days Saturday -Months February, May, August, December |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Set-VBRJobSchedule cmdlet. Specify the following settings:  * Set the $job variable as the Job parameter value. * Provide the Monthly parameter. * Specify the At parameter value. * Specify the NumberInMonth parameter value. * Specify the Days parameter value. * Specify the Months parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Scheduling Job to Run Every Several Hours

|  |  |
| --- | --- |
| This example shows how to schedule the Daily Job to run every 12 hours.  |  | | --- | | $job = Get-VBRJob -Name "Daily Job"  Set-VBRJobSchedule -Job $job -Periodicaly -FullPeriod 12 -PeriodicallyKind Hours |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the Set-VBRJobSchedule cmdlet. Specify the following settings:  * Set the $job variable as the Job parameter value. * Provide the Periodicaly parameter. * Specify the FullPeriod parameter value. * Specify the PeriodicallyKind parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Scheduling Job to Run After Another Job

|  |  |
| --- | --- |
| This example shows how to schedule the Daily Job to run after the Database Job.  |  | | --- | | $dbjob = Get-VSBJob -Name "Database Job"  $dailyjob = Get-VBRJob -Name "Daily Job"  Set-VBRJobSchedule -Job $dailyjob -After -AfterJob $dbjob |  Perform the following steps:   1. Run the [Get-VSBJob](get-vsbjob.md) cmdlet. Specify the Name parameter value. Save the result to the $dbjob variable. 2. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $dailyjob variable. 3. Run the Set-VBRJobSchedule cmdlet. Specify the following settings:  * Set the $dailyjob variable as the Job parameter value. * Provide the After parameter. * Set the $dbjob as the AfterJob parameter value. |

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [Get-VSBJob](get-vsbjob.md)

Page updated 8/8/2024

Page content applies to build 13.0.1.1071
