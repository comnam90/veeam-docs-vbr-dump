---
title: "Set-VBRJobAdvancedOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrjobadvancedoptions.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# Set-VBRJobAdvancedOptions

In this article

Short Description

Customizes advanced job settings.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRJobAdvancedOptions [-CommandLine <String>] [-CompactFullMonthlyOptions <VBRMonthlyOptions>] [-CompactFullScheduleType {Weekly | Monthly}] [-CompactFullWeeklyOptions <VBRDailyOptions>] [-Days <DayOfWeek[]>] [-EnableCompactFull] [-Enabled [<Boolean>]] [-EnableHealthCheck] [-EnableIntegrityChecks <Boolean>] [-EnablePreScript <Boolean>] [-Frequency <UInt32>] -Job <CBackupJob[]> [-Periodicity {Cycles | Days}] [-PreJobScript <String>] [-RetainDays <Int32>]  [<CommonParameters>] |

Detailed Description

This cmdlet sets advanced options for the selected job.

You can set:

* Integrity check: Veeam Backup & Replication will check every full backup file for integrity and recovery availability.
* Post job activity: you can specify a command you want to run after the job run, i.e. to sent a job result report. You can schedule this command to run i.e. every second job run or on specific days.
* Deleted VMs retention period: if a VM included in this job is deleted, its data will be stored for the specified period. When this period ends, the backup files are deleted. The default period is 14 days.

Read more about advanced job settings in [Veeam Backup & Replication User Guide](https://helpcenter.veeam.com/docs/vbr/userguide/backup_job_advanced_maintenance_vm.html?ver=13).

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameters values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of jobs. The cmdlet will modify advanced options of these jobs. | Accepts the CBackupJob[] object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByProperty Name, ByValue) |
| EnableIntegrityChecks | Defines whether the job will use the automatic backup integrity check. | Bool | False | Named | False |
| EnableHealthCheck | Enables the Health check option. | SwitchParameter | False | Named | False |
| RetainDays | Specifies the number of days to keep backup data for the deleted VMs.  Default: 14 days.  Note: You cannot enable the retention policy for deleted VMs with Veeam PowerShell. To learn how to do this in Veeam Backup & Replication console, see the [Retention Policy for Deleted VMs](https://helpcenter.veeam.com/docs/vbr/userguide/retention_deleted_vms.html?ver=13) section in User Guide. | Int32 | False | Named | False |
| Enabled | Defines whether the job will execute a user-defined command after the job.  Use the CommandLine parameter to set the command.  Schedule the command to run periodically with the Periodicity and Frequency parameters, or on specific days with the Days parameter. | Bool | False | Named | False |
| CommandLine | Specifies the command you want to execute after the job. | String | False | Named | False |
| CompactFullMonthlyOptions | For a monthly schedule.  Specifies a monthly schedule for a job. | Accepts the VBRMonthlyOptions object. To create this object, run the [New-VBRMonthlyOptions](new-vbrmonthlyoptions.md) cmdlet. | False | Named | False |
| CompactFullScheduleType | Specifies the type of the job schedule. Parameter accepts the following values:   * Monthly: the job will run on selected days of the month. * Weekly: the job will run on selected days of the week. | VBRAdvancedOptionsScheduleType | False | Named | False |
| CompactFullWeeklyOptions | For a weekly schedule.  Specifies a weekly schedule for a job. | Accepts the VBRDailyOptions object. To create this object, run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. | False | Named | False |
| EnableCompactFull | Enables the Defragment and compact full backup file option. | SwitchParameter | False | Named | False |
| EnablePreScript | Defines whether the job will execute a user script before the job starts.  Use the PreJobScript parameter to specify the script. | Bool | False | Named | False |
| PreJobScript | Specifies the script you want to run before job. | String | False | Named | False |
| Periodicity | For command schedule.  Specifies the command schedule type:   * Cycles: the command will be executed in periods set with the Frequency parameter. * Days: the command will be executed on the days specified with the Days parameter. | PeriodicityType | False | Named | False |
| Frequency | For command cycle schedule.  Specifies the number of the backup cycles after which the command will be executed (for example, every 3 backup cycle). | UInt32 | False | Named | False |
| Days | For command schedule on days.  Specifies the days to run the command:   * Sunday * Monday * Tuesday * Wednesday * Thursday * Friday * Saturday | DayOfWeek[] | False | Named | False |
| HealthCheckMonthlyOptions | Specifies health check monthly options. | VBRMonthlyOptions | False | Named | False |
| HealthCheckScheduleType | Specifies the type of the health check schedule. Parameter accepts the following values:   * Monthly: the health check will run on selected days of the month. * Weekly: the health check will run on selected days of the week. | VBRAdvancedOptionsScheduleType | False | Named | False |
| HealthCheckWeeklyOptions | Specifies health check weekly options. | VBRDailyOptions | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Editing Advanced Job Settings to Specific Backup Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to edit advanced job settings to backup job named Backup Job 01:   * The integrity check is enabled. * The data retention period is set to 30 days.   |  | | --- | | Get-VBRJob -Name "Backup Job 01" | Set-VBRJobAdvancedOptions -EnableIntegrityChecks $True -RetainDays 30 |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Set-VBRJobAdvancedOptions cmdlet. Provide the $True value for the EnableIntegrityChecks parameter. Specify the RetainDays parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Editing Advanced Job Settings to Specific Backup Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to edit advanced job settings to backup job named Backup Job 01:   * The integrity check is enabled. * The data retention is not set to leave the default settings. * The post job activity is enabled to run the report.exe command periodically after every fifth job run.   |  | | --- | | Get-VBRJob -Name "Backup Job 01" | Set-VBRJobAdvancedOptions -EnableIntegrityChecks $True -Enabled $True -CommandLine "report.exe" -Periodicity Cycles -Frequency 5 |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Set-VBRJobAdvancedOptions cmdlet. Specify the following settings:  * Provide the $True value for the EnableIntegrityChecks parameter. * Provide the $True value for the Enabled parameter. * Specify the CommandLine parameter value. * Set the Cycles option for the Periodicity parameter. * Specify the Frequency parameter value. |

Related Commands

[Get-VBRJob](get-vbrjob.md)

Page updated 11/18/2025

Page content applies to build 13.0.1.1071
