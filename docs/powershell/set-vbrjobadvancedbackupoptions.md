---
title: "Set-VBRJobAdvancedBackupOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrjobadvancedbackupoptions.html"
last_updated: "10/14/2025"
product_version: "13.0.1.1071"
---

# Set-VBRJobAdvancedBackupOptions

In this article

Short Description

Modifies advanced job backup settings.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRJobAdvancedBackupOptions -Job <CBackupJob[]> [-Algorithm {ReverseIncremental | Incremental | RecoveryPointObjective | Unknown}] [-TransformFullToSynthetic <Boolean>] [-TransformToSyntheticScheduleKind <EFullBackupScheduleKind>] [-TransformToSyntheticDays {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-TransformToSyntheticMonths {January | February | March | April | May | June | July | August | September | October | November | December}] [-SyntheticDayNumberInMonth {First | Second | Third | Fourth | Last | OnDay}] [-SyntheticDayOfMonth <CDayOfMonth>] [-SyntheticDayOfWeek {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-EnableFullBackup <Boolean>] [-FullBackupDays {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}] [-FullBackupScheduleKind {Daily | Monthly}] [-Months {January | February | March | April | May | June | July | August | September | October | November | December}] [-DayNumberInMonth {First | Second | Third | Fourth | Last | OnDay}] [-DayOfMonth <CDayOfMonth>] [-DayOfWeek {Sunday | Monday | Tuesday | Wednesday | Thursday | Friday | Saturday}]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies advanced backup options of a selected job.

You can select backup method: reverse incremental or incremental, and set schedule settings for synthetic full backups.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameters values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of jobs. The cmdlet will modify advanced backup options of these jobs. | Accepts the CBackupJob[] object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | Named | True (ByProperty Name, ByValue) |
| Algorithm | Specifies backup method:   * ReverseIncremental: reverse incremental backup method. * Incremental: incremental backup method.  * RecoveryPointObjective: not supported. * Unknown: not supported.   Note: To enable forever forward incremental backup method, disable the TransformFullToSynthetic and EnableFullBackup parameters. | JobAlgorithms | False | Named | False |
| TransformFullToSynthetic | For incremental backup method.  Defines whether the job will create a synthetic full backup.  Use the TransformToSyntheticDays parameter to set the days to perform the synthetic full backups. | Bool | False | Named | False |
| TransformToSyntheticScheduleKind | For synthetic full schedule.  Specifies the synthetic full backup schedule type:   * Daily: the job will create a synthetic full on selected days of week. Use the TransformToSyntheticDays parameter to set the days. * Monthly: the job will create a synthetic full on selected days of month. Use the TransformToSyntheticMonths, SyntheticDayNumberInMonth and SyntheticDayOfMonth parameters to configure the schedule. | EFullBackupScheduleKind | False | Named | False |
| TransformToSyntheticDays | For synthetic full schedule.  Specifies days when the job will perform the synthetic fulls:   * Sunday * Monday * Tuesday * Wednesday * Thursday * Friday * Saturday | DayOfWeek[] | False | Named | False |
| TransformToSyntheticMonths | For synthetic full schedule: monthly.  Specifies months to perform the synthetic full backup:   * January * February * March * April * May * June * July * August * September * October * November * December | EMonth[] | False | Named | False |
| SyntheticDayOfWeek | Specifies the day of week to run the backup job:   * Sunday * Monday * Tuesday * Wednesday * Thursday * Friday * Saturday   Use this parameter to set the day for the SyntheticDayNumberInMonth parameter, for example, to run the job on first Saturday every month. | DayOfWeek | False | Named | False |
| SyntheticDayOfMonth | For synthetic full schedule: monthly with the SyntheticDayNumberInMonth parameter set to OnDay.  Specifies the day of month to perform an active full backup. | CDayOfMonth | False | Named | False |
| SyntheticDayNumberInMonth | Specifies the number of day in month (for example, Saturday):   * First: the job will create a synthetic full on the first (Saturday) of the selected months. * Second: the job will create a synthetic full on the second (Saturday) of the selected months. * Third: the job will create a synthetic full on the third (Saturday) of the selected months. * Fourth: the job will create a synthetic full on the fourth (Saturday) of the selected months. * Last: the job will create a synthetic full on the last (Saturday) of the selected months. * OnDay: the job will create a synthetic full backup on a specific day of month. Use the SyntheticDayOfMonth parameter to specify the day of month. | EDayNumberInMonth | False | Named | False |
| EnableFullBackup | Defines whether the job will create active full backups.  Use the FullBackupDays, FullBackupScheduleKind, Months, DayNumberInMonth and DayOfWeek parameters to set the full backup schedule. | Bool | False | Named | False |
| FullBackupDays | For active full schedule: daily.  Specifies days when the job will perform the active full backup:   * Sunday * Monday * Tuesday * Wednesday * Thursday * Friday * Saturday | DayOfWeek[] | False | Named | False |
| FullBackupScheduleKind | For active full schedule.  Specifies the active full backup schedule type:   * Daily: the job will create an active full on selected days of week. Use the FullBackupDays parameter to set the days. * Monthly: the job will create an active full on selected days of month. Use the Months, DayNumberInMonth and DayOfWeek parameters to set the days. | EFullBackupScheduleKind | False | Named | False |
| Months | For active full schedule: monthly.  Specifies months to perform the full backup:   * January * February * March * April * May * June * July * August * September * October * November * December | EMonth[] | False | Named | False |
| DayNumberInMonth | For active full schedule: monthly.  Specifies the number of day in month (for example, Saturday):   * First: the job will create an active full on the first (Saturday) of the selected months. * Second: the job will create an active full on the second (Saturday) of the selected months. * Third: the job will create an active full on the third (Saturday) of the selected months. * Fourth: the job will create an active full on the fourth (Saturday) of the selected months. * Last: the job will create an active full on the last (Saturday) of the selected months. * OnDay: the job will create an active full backup on a specific day of month. Use the DayOfMonth parameter to specify the day of month. | EDayNumberInMonth | False | Named | False |
| DayOfMonth | For active full schedule: monthly with the OnDay option.  Specifies the day of month to perform an active full backup. | CDayOfMonth | False | Named | False |
| DayOfWeek | Sets backup schedule.  Specifies the day of week to run the backup job:   * Sunday * Monday * Tuesday * Wednesday * Thursday * Friday * Saturday   Use this parameter to set the day for the NumberInMonth parameter,  i.e. to run the job on first Saturday every month. | DayOfWeek[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Setting Specific Backup Options for Backup Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to set the following backup options for the backup job represented by the $job variable:   * The backup algorithm is set to ReverseIncremental. * The active full backup schedule is set to monthly.   |  | | --- | | $job = Get-VBRJob -Name "Backup Job"  $job | Set-VBRJobAdvancedBackupOptions -Algorithm ReverseIncremental -FullBackupScheduleKind Monthly |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Pipe the cmdlet output to the Set-VBRJobAdvancedBackupOptions cmdlet. Set the ReverseIncremental option for the Algorithm parameter. Set the Monthly option for the FullBackupScheduleKind parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Setting Specific Backup Options for all Backup Jobs [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to set the following backup options for all backup jobs:   * The backup algorithm is set to Incremental. * The synthetic full backup is enabled on every Sunday and Thursday. * The active full backup schedule is set to every second Sunday monthly.   |  | | --- | | Get-VBRJob -Name Backup\* | Set-VBRJobAdvancedBackupOptions -Algorithm Incremental -TransformFullToSynthetic $True -TransformToSyntheticDays Sunday, Thursday -EnableFullBackup $True -FullBackupScheduleKind Monthly -DayNumberInMonth Second -FullBackupScheduleKind Daily -DayOfWeek Sunday |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Set-VBRJobAdvancedBackupOptions cmdlet. Specify the following settings:  * Set the Incremental option for the Algorithm parameter. * Provide the $True value for the TransformFullToSynthetic parameter. * Specify the TransformToSyntheticDays parameter value. * Provide the $True value for the EnableFullBackup parameter. * Set the Monthly option for the FullBackupScheduleKind parameter. * Specify the DayNumberInMonth parameter value. * Set the Daily option for the FullBackupScheduleKind parameter value. * Specify the DayOfWeek parameter value. |

Related Commands

[Get-VBRJob](get-vbrjob.md)

Page updated 10/14/2025

Page content applies to build 13.0.1.1071
