---
title: "Set-VBRSureBackupJobScheduleOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrsurebackupjobscheduleoptions.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Set-VBRSureBackupJobScheduleOptions


Short Description

Modifies settings of a SureBackup job schedule.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRSureBackupJobScheduleOptions -VBRSbJobScheduleOptions <VBRSureBackupJobScheduleOptions> [-Type <VBRSbJobScheduleType> {Daily | Monthly | AfterJob}] [-DailyOptions <VBRDailyOptions>] [-MonthlyOptions <VBRMonthlyOptions>] [-ParentJob <CBackupJob>] [-WaitForParentJob] [-WaitTimeMinutes <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of a SureBackup job schedule.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| VBRSbJobScheduleOptions | Specifies the SureBackup job schedule. The cmdlet will modify this schedule. | Accepts the VBRSureBackupJobScheduleOptions object. To create this object, run the [New-VBRSureBackupJobScheduleOptions](new-vbrsurebackupjobscheduleoptions.md) cmdlet. | True | Named | False |
| Type | Specifies how often a SureBackup job must run. You can select one of the following options:   * Daily: use this option if you want the SureBackup job to run every day. * Monthly: use this option if you want the SureBackup job to run monthly. * AfterJob: use this option if you want the SureBackup job to run after a specific job. Provide the ParentJob parameter to specify the job after which the SureBackup job must run. | VBRSbJobScheduleType | True | Named | False |
| DailyOptions | For a daily schedule.  Specifies a daily schedule for a SureBackup job. The cmdlet will create the SureBackup job with this schedule. | Accepts the VBRDailyOptions object. To create this object, run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. | False | Named | False |
| MonthlyOptions | For a monthly schedule.  Specifies a monthly schedule for a SureBackup job. The cmdlet will create the SureBackup job with this schedule. | Accepts the VBRMonthlyOptions object. To create this object, run the [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md) cmdlet. | False | Named | False |
| ParentJob | For running after a job.  Specifies a name of the job after which Veeam Backup & Replication the SureBackup job must run. The cmdlet will create the SureBackup job with this schedule. | Accepts the CBackupJob object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | False | Named | False |
| WaitForParentJob | Defines that the SureBackup job will wait until the linked backup or replication job completes.  If you provide this parameter, Veeam Backup & Replication will wait until the linked job completes. Otherwise, it will start the SureBackup job without waiting for the linked job to complete.  Use the WaitTimeMinutes parameter to specify how long the SureBackup job must wait for the linked job to complete. | SwitchParamter | False | Named | False |
| WaitTimeMinutes | Specifies the time period in minutes that the SureBackup job must wait for the linked job to complete. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSureBackupJobScheduleOptions object that defines SureBackup job schedule.

Examples

Modifying Daily SureBackup Job Schedule

This example shows how to modify the daily SureBackup job schedule. The schedule is modified to run the SureBackup job every Saturday at 23:00.

|  |
| --- |
| $daily = New-VBRDailyOptions -DayOfWeek Friday -Period 23:00  $schedule = New-VBRSureBackupJobScheduleOptions -Type Daily -DailyOptions $daily  $dailynew = New-VBRDailyOptions -DayOfWeek Saturday -Period 23:00  Set-VBRSureBackupJobScheduleOptions -VBRSbJobScheduleOptions $schedule -Type Daily -DailyOptions $dailynew |

Perform the following steps:

1. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Specify the DayOfWeek parameter value. Specify the Period parameter value. Save the result to the $daily variable.
2. Run the [New-VBRSureBackupJobScheduleOptions](new-vbrsurebackupjobscheduleoptions.md) cmdlet. Set the Daily option for the Type parameter value. Set the $daily variable as the DailyOptions parameter value. Save the result to the $schedule variable.
3. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Specify the DayOfWeek parameter value. Specify the Period parameter value. Save the result to the $dailynew variable.
4. Run the Set-VBRSureBackupJobScheduleOptions cmdlet. Specify the following settings:

* Set the $schedule variable as the VBRSbJobScheduleOptions parameter value.
* Set the Daily options for the Type parameter value.
* Set the $dailynew variable as the DailyOptions parameter value.

Related Commands

* [New-VBRDailyOptions](new-vbrdailyoptions.md)
* [New-VBRSureBackupJobScheduleOptions](new-vbrsurebackupjobscheduleoptions.md)


