---
title: "Set-VSBJobSchedule (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vsbjobschedule.html"
last_updated: "6/3/2024"
product_version: "13.0.1.1071"
---

# Set-VSBJobSchedule (obsolete)

In this article

Short Description

Modifies SureBackup job schedule options.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet will still work but may not be supported in further versions. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VSBJobSchedule -Job <CSbJob> [-Daily] [-At <DateTime>] [-DailyKind <DailyOptions+DailyKinds>] [-Days <DayOfWeek[]>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>]  -OR-  Set-VSBJobSchedule -Job <CSbJob> [-At <DateTime>] [-Days <DayOfWeek[]>] [-Monthly] [-NumberInMonth <EDayNumberInMonth>] [-Months <EMonth[]>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>]  -OR-  Set-VSBJobSchedule -Job <CSbJob> [-After] [-AfterJob <CBackupJob>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies schedule settings of a SureBackup job.

You can schedule the job to run:

* Daily on specific time, on specific days of week.
* Monthly on specific time, on specific days of month, on specific months.
* After a certain job you specify.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the SureBackup job. The cmdlet will modify settings of this job. | Accepts the CSbJob object. To get this object, run the [Get-VSBJob](get-vsbjob.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Daily | For daily schedule.  Defines that the SureBackup job runs daily. Use At and DailyKind parameters to specify the daily schedule. | SwitchParameter | False | Named | False |
| At | For daily schedule.  Specifies the SureBackup job start time.  Default: 10:00. | DateTime | False | Named | False |
| DailyKind | For daily schedule.  Specifies the days when the SureBackup job runs:   * Everyday: the job will run everyday * WeekDays: the job will run Monday through Friday * SelectedDays: the job will run on specific days (for example, on Saturdays). Use the Days parameter to set the specific days | DailyOptions+DailyKinds | False | Named | False |
| Days | For daily schedule.  Specifies the days of week when the SureBackup job runs. | DayOfWeek[] | False | Named | False |
| At | For monthly schedule.  Specifies the SureBackup job start time.  Default: 10:00. | DateTime | False | Named | False |
| Days | For monthly schedule.  Specifies the day of week when the SureBackup job runs. Use this parameter to set the day for NumberInMonth parameter, for example, on first Saturday every month. | DayOfWeek[] | False | Named | False |
| NumberInMonth | For monthly schedule.  Specifies the number of day in month (for example, Saturday):   * First: the SureBackup job runs on the first (Saturday) of the selected months. * Second: the SureBackup job runs on the second (Saturday) of the selected months. * Third: the SureBackup job runs on the third (Saturday) of the selected months. * Fourth: the SureBackup job runs on the fourth (Saturday) of the selected months. * Last: the SureBackup job runs on the last (Saturday) of the selected months. | EDayNumberInMonth | False | Named | False |
| Monthly | For monthly schedule.  Defines that the SureBackup job runs once a month. Use Months, NumberInMonth and  Days parameters to set the monthly schedule. | SwitchParameter | False | Named | False |
| Months | For monthly schedule.  Specifies the months when the SureBackup job runs. | EMonth[] | False | Named | False |
| After | After this job.  Defines that the SureBackup job runs after a selected job. Use the AfterJob parameter to specify the primary job. | SwitchParameter | False | Named | False |
| AfterJob | After this job.  Specifies the job after which the SureBackup job runs. | Accepts the CBackupJob object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Scheduling SureBackup Jobs to Run Daily

|  |  |
| --- | --- |
| This example shows how to schedule the SureBackup Job 01 and SureBackup Job 05 jobs to run daily at 23:00 on weekdays.  |  | | --- | | Get-VSBJob -Name "SureBackup Job 01", "SureBackup Job 05" | Set-VSBJobSchedule -Daily -At "23:00" -DailyKind Weekdays |  Perform the following steps:   1. Run the Get-VSBJob cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Set-VSBJobSchedule cmdlet. Provide the Daily parameter. Specify the At parameter value. Set the Weekdays option for the DailyKind parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Scheduling SureBackup Jobs to Run Last Saturday of Specific Months

|  |  |
| --- | --- |
| This example shows how to schedule the SureBackup Job 01 and SureBackup Job 05 jobs to run daily at 23:00 on weekdays.  |  | | --- | | Get-VSBJob -Name \*SureJob\* | Set-VSBJobSchedule -Monthly -At "12:00" -NumberInMonth Last -Days Saturday  -Months February, May, August, December |  Perform the following steps:   1. Run the Get-VSBJob cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Set-VSBJobSchedule cmdlet. Specify the following settings:  * Provide the Monthly parameter. * Specify the At parameter value. * Set the Last option for the NumberInMonth parameter value. * Set the Saturday option for the Days parameter value. * Set the February, May, August, December options for the Months parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Scheduling SureBackup Jobs to Run After Specific Job

|  |  |
| --- | --- |
| This example shows how to schedule the SureBackup Job 01 job to run after the job.  |  | | --- | | $job = Get-VBRJob -Name "VM Backup Job"  Get-VSBJob -Name "SureBackup Job 01" | Set-VSBJobSchedule -After -AfterJob $job |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [Get-VSBJob](get-vsbjob.md) cmdlet. Specify the Name parameter value. 3. Pipe the cmdlet output to the Set-VSBJobSchedule cmdlet. Provide the After parameter. Set the $job variable as the AfterJob parameter value. |

Related Commands

* [Get-VSBJob](get-vsbjob.md)
* [Get-VBRJob](get-vbrjob.md)

Page updated 6/3/2024

Page content applies to build 13.0.1.1071
