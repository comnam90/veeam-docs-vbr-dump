---
title: "Set-VBRServerScheduleOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrserverscheduleoptions.html"
last_updated: "5/6/2024"
product_version: "13.0.1.1071"
---

# Set-VBRServerScheduleOptions


Short Description

Modifies the schedule for Veeam Agent backup jobs.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRServerScheduleOptions -Options <VBRServerScheduleOptions> [-Type <VBRServerScheduleType> {Daily | Monthly |Periodically | AfterJob}] [-DailyOptions <VBRDailyOptions>] [-MonthlyOptions <VBRMonthlyOptions>] [-PeriodicallyOptions <VBRPeriodicallyOptions>] [-Job <CBackupJob>] [-EnableRetry] [-RetryCount <int>] [-RetryTimeout <int>] [-EnableBackupTerminationWindow] [-TerminationWindow <VBRBackupWindowOptions>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies schedule settings for the following types of jobs:

* Veeam Agent jobs that back up Linux servers.
* Veeam Agent jobs that back up failover clusters.
* Veeam Agent jobs that back up Windows servers.
* The backup policy that Veeam Agent job applies to Windows servers.

|  |
| --- |
| Important |
| Consider the following:   * For Veeam Agent jobs that back up Linux workstations, use the [New-VBRLinuxScheduleOptions](new-vbrlinuxscheduleoptions.md) cmdlet. * For the backup policy that Veeam Agent jobs applies to Windows workstations, use the [New-VBRWindowsWorkstationScheduleOptions](new-vbrwindowsworkstationscheduleoptions.md) cmdlet. |

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Options | Specifies the server schedule settings that you want to modify. | Accepts the VBRServerScheduleOptions object. To get this object, run the [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) cmdlet. | True | Named | True (ByValue) |
| Type | Specifies the Veeam Agent backup job schedule type.   * Daily: use this option to run the job at a specific time daily. * Monthly: use this option to run the job once a month on specific days. * Periodically: use this option to run the job repeatedly throughout a day with a specific time interval. * AfterJob: use this option to create a chain of jobs. Veeam Backup & Replication will start the Veeam Agent Backup job after the other backup job. | VBRServerScheduleType | False | Named | False |
| DailyOptions | For daily schedule.  Specifies daily schedule settings. The cmdlet will create the server schedule with these settings. | Accepts the [VBRDailyOptions](vbrdailyoptions.md) object. To get this object, run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. | False | Named | False |
| MonthlyOptions | For monthly schedule.  Specifies monthly schedule settings. The cmdlet will create the server schedule with these settings. | Accepts the [VBRMonthlyOptions](vbrmonthlyoptions.md) object. To get this object, run the [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md) cmdlet. | False | Named | False |
| PeriodicallyOptions | For periodical run.  Specifies periodical schedule settings. The cmdlet will create the server schedule with these settings. | Accepts the [VBRPeriodicallyOptions](vbrperiodicallyoptions.md) object. To get this object, run the [New-VBRPeriodicallyOptions](new-vbrperiodicallyoptions.md) cmdlet. | False | Named | False |
| Job | For running after a job.  Specifies the name of the backup job after which Veeam Backup & Replication will run Veeam Agent backup jobs. The cmdlet will create the server schedule with these settings. | Accepts the CBackupJob object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | False | Named | False |
| EnableRetry | Enables the option to run the Veeam Agent backup job again in case it fails. | SwitchParameter | False | Named | False |
| RetryCount | For the EnableRetry parameter.  Specifies the number of attempts to run the failed Veeam Agent backup job. | Int | False | Named | False |
| RetryTimeout | For the EnableRetry parameter.  Specifies the time interval between retry attempts in minutes. | Int | False | Named | False |
| EnableBackupTerminationWindow | Enables the option to stop the Veeam Agent backup job if it exceeds the backup window. | SwitchParameter | False | Named | False |
| TerminationWindow | Specifies the time interval within which the backup job must complete. The cmdlet will create the Veeam Agent backup job with these settings. | Accepts the VBRBackupWindowOptions object. To create this object, run the [New-VBRBackupWindowOptions](new-vbrbackupwindowoptions.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRServerScheduleOptions object that contains schedule settings for backup jobs.

Examples

Modifying Schedule for Veeam Agent Backup Job

This example shows how to modify an existing schedule for a Veeam Agent backup job.

|  |
| --- |
| $job = Get-VBRComputerBackupJob -Name "BackupJob"  $options = New-VBRServerScheduleOptions -Type Daily -DailyOptions $daily  $period = New-VBRPeriodicallyOptions -FullPeriod 12 -PeriodicallyKind Hours  $termination = New-VBRBackupWindowOptions -FromDay Friday -FromHour 17 -ToDay Monday -ToHour 8  Set-VBRServerScheduleOptions -Options $options -Type Periodically -PeriodicallyOptions $period -EnableBackupTerminationWindow -TerminationWindow $termination |

Perform the following steps:

1. Run the [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable.
2. Run the [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) cmdlet. Set the Daily value as the Type parameter value. Set the $daily variable as the DailyOptions parameter value. Save the result to the $options variable.
3. Run the [New-VBRPeriodicallyOptions](new-vbrperiodicallyoptions.md) cmdlet. Specify the FullPeriod and PeriodicallyKind parameter values. Save the result to the $period variable.
4. Run the [New-VBRBackupWindowOptions](new-vbrcloudfailoverplanobject.md) cmdlet. Specify the FromDay, FromHour, ToDay and ToHour parameter values. Save the result to the $termination variable.
5. Run the Set-VBRServerScheduleOptions cmdlet. Specify the following settings:

* Set the $options variable as the Options parameter value.
* Set the Periodically option for the Type parameter.
* Set the $period variable as the PeriodicallyOptions parameter value.
* Provide the EnableBackupTerminationWindow parameter.
* Set the $termination variable as the TerminationWindow parameter value.

Related Commands

* [Get-VBRComputerBackupJob](get-vbrcomputerbackupjob.md)
* [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md)
* [New-VBRPeriodicallyOptions](new-vbrperiodicallyoptions.md)
* [New-VBRBackupWindowOptions](new-vbrcloudfailoverplanobject.md)


