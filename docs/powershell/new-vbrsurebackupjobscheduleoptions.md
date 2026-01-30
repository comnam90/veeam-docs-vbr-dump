---
title: "New-VBRSureBackupJobScheduleOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrsurebackupjobscheduleoptions.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# New-VBRSureBackupJobScheduleOptions


Short Description

Defines a SureBackup job schedule.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRSureBackupJobScheduleOptions -Type <VBRSbJobScheduleType> {Daily | Monthly | AfterJob} [-DailyOptions <VBRDailyOptions>] [-MonthlyOptions <VBRMonthlyOptions>] [-ParentJob <CBackupJob>] [-WaitForParentJob] [-WaitTimeMinutes <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRSureBackupJobScheduleOptions object that defines a SureBackup job schedule.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Type | Specifies how often a SureBackup job must run. You can select one of the following options:   * Daily: use this option if you want the SureBackup job to run every day. * Monthly: use this option if you want the SureBackup job to run monthly. * AfterJob: use this option if you want the SureBackup job to run after a specific job. Provide the ParentJob parameter to specify the job after which the SureBackup job must run. | VBRSbJobScheduleType | True | Named | False |
| DailyOptions | For daily schedule.  Specifies a daily schedule for a SureBackup job. The cmdlet will create the SureBackup job with this schedule. | Accepts the VBRDailyOptions object. To create this object, run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. | False | Named | False |
| MonthlyOptions | For a monthly schedule.  Specifies a monthly schedule for a SureBackup job. The cmdlet will create the SureBackup job with this schedule. | Accepts the VBRMonthlyOptions object. To create this object, run the [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md) cmdlet. | False | Named | False |
| ParentJob | For running after a job.  Specifies a name of the job after which Veeam Backup & Replication the SureBackup job must run. The cmdlet will create the SureBackup job with this schedule. | Accepts the CBackupJob object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | False | Named | False |
| WaitForParentJob | Defines that the SureBackup job will wait until the linked backup or replication job completes.  If you provide this parameter, Veeam Backup & Replication will wait until the linked job completes. Otherwise, it will start the SureBackup job without waiting for the linked job to complete.  Use the WaitTimeMinutes parameter to specify how long the SureBackup job must wait for the linked job to complete. | SwitchParamter | False | Named | False |
| WaitTimeMinutes | Specifies the time period in minutes that the SureBackup job must wait for the linked job to complete. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSureBackupJobScheduleOptions object that defines SureBackup job schedule.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Daily SureBackup Job Schedule

|  |  |
| --- | --- |
| This example shows how to define the daily SureBackup job schedule. The schedule is created to run the SureBackup job every Friday at 23:00.  |  | | --- | | $daily = New-VBRDailyOptions -DayOfWeek Friday -Period 23:00  New-VBRSureBackupJobScheduleOptions -Type Daily -DailyOptions $daily |  Perform the following steps:   1. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Specify the DayOfWeek parameter value. Specify the Period parameter value. Save the result to the $daily variable. 2. Run the New-VBRSureBackupJobScheduleOptions cmdlet. Set the Daily option for the Type parameter value. Set the $daily variable as the DailyOptions parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Monthly SureBackup Job Schedule

|  |  |
| --- | --- |
| This example shows how to define the monthly SureBackup job schedule. The schedule is created to run the SureBackup job at 23:00 on the second Wednesday every month.  |  | | --- | | $monthly = New-VBRMonthlyOptions -DayNumberInMonth Second -DayOfWeek Wednesday -Period 23:00  New-VBRSureBackupJobScheduleOptions -Type Monthly MonthlyOptions $monthly |  Perform the following steps:   1. Run the [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md) cmdlet. Set the Second option for the DayNumberInMonth parameter value. Set the Wednesday option for the DayOfWeek parameter value. Specify the Period parameter value. Save the result to the $monthly variable. 2. Run the New-VBRSureBackupJobScheduleOptions cmdlet. Set the Monthly option for the Type parameter value. Set the $monthly variable as the DailyOptions parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Defining Chained SureBackup Job Schedule

|  |  |
| --- | --- |
| This example shows how to define the chained SureBackup job schedule. The schedule is created to run the SureBackup job after the Exchange Backup Job job completes.  |  | | --- | | $job = Get-VBRJob -Name "Exchange Backup Job"  New-VBRSureBackupJobScheduleOptions -Type AfterJob -ParentJob $job |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the New-VBRSureBackupJobScheduleOptions cmdlet. Set the AfterJob option for the Type parameter value. Set the $job variable as the ParentJob parameter value. |

Related Commands

* [New-VBRDailyOptions](new-vbrdailyoptions.md)
* [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md)
* [Get-VBRJob](get-vbrjob.md)


