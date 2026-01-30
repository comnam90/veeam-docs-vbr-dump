---
title: "New-VBRBackupWindowOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrbackupwindowoptions.html"
last_updated: "11/18/2025"
product_version: "13.0.1.1071"
---

# New-VBRBackupWindowOptions


Short Description

Defines backup window settings for a job.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRBackupWindowOptions [-Enabled] [-FromDay <DayOfWeek>] [-FromHour <Int32>] [-ToDay <DayOfWeek>] [-ToHour <Int32>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRBackupWindowOptions object. This object contains backup window settings for a job. These settings define a time interval within which the job must be completed. You can apply these settings to a job.

For more information on the backup windows option, see the [Backup Window](https://helpcenter.veeam.com/docs/vbr/userguide/backup_window.html?ver=13) section in the User Guide for VMware vSphere.

Run the [Set-VBRJobSchedule](set-vbrjobschedule.md) cmdlet to apply backup window settings to the backup, replication or backup copy job.

Run the [New-VBRBackupToTapeScheduleOptions](new-vbrbackuptotapescheduleoptions.md) cmdlet to apply backup window settings to a backup to tape job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| FromDay | Specifies the day of week on which the backup window opens.  Default: Sunday. | DayOfWeek | False | Named | False |
| FromHour | Specifies an hour when the backup window opens.  Default: 0. | Int32 | False | Named | False |
| ToDay | Specifies the day of week on which the backup window closes.  Default: Saturday. | DayOfWeek | False | Named | False |
| ToHour | Specifies an hour when the backup window closes.  Note: The backup windows closes at the end of an hour that you specify in the ToHour parameter.  For example, if you specify the 22 value for the ToHour parameter, the backup window will end at 22:59.  Default: 23. | Int32 | False | Named | False |
| Enabled | Defines that the cmdlet will enable the backup window.  If you provide this parameter, the period that you set for a backup window will specify the time when the job is allowed to run.  Otherwise, the period that you set for a backup window will specify the time when the job is not allowed to run. | SwitchParameter | False | Named | True (ByProperty Name, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Backup Window Settings

|  |  |
| --- | --- |
| This command defines backup window settings that will allow a job to run from 20:00 to 22:59 every day from Monday to Friday.  |  | | --- | | $windowoptions = New-VBRBackupWindowOptions -FromDay Monday -ToDay Friday -FromHour 20 -ToHour 22 -Enabled | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Backup Window Settings for Specific Period of Time

|  |  |
| --- | --- |
| This command defines backup window settings that will allow a job to run during the following period of time:   * From 22:00 to 22:59 on Friday * From 22:00 to 22:59 on Saturday   |  | | --- | | $windowoptions = New-VBRBackupWindowOptions -FromDay Friday -FromHour 22 -ToDay Saturday -ToHour 22 -Enabled | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Defining Period of Time When Job must not Run

|  |  |
| --- | --- |
| This command defines backup window settings for a job. These settings specify the period of time when the job must not run. According to these setting the job is not allowed to run from 08:00 to 20:59 on weekdays.  |  | | --- | | $windowoptions = New-VBRBackupWindowOptions -FromDay Monday -FromHour 8 -ToDay Friday -ToHour 20 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Modifying Schedule Settings of Existing Job

|  |  |
| --- | --- |
| This example shows how to modify schedule settings of an existing job. The job is allowed to run from 07:00 to 19:59 every day from Sunday to Monday except for Saturday.  |  | | --- | | $windowoptions = New-VBRBackupWindowOptions -FromDay Friday -FromHour 19 -ToDay Sunday -ToHour 7 -Enabled  $job = Get-VBRJob -Name "SQL Backup Job"  Set-VBRJobSchedule -Job $job -Periodicaly -FullPeriod 6 -PeriodicallyKind Hours -PeriodicallySchedule $windowoptions |  Perform the following steps:   1. Run the New-VBRBackupWindowOptions cmdlet. Specify the following settings:  * Specify the FromDay parameter value. * Specify the FromHour parameter value. * Specify the ToDay parameter value. * Specify the ToHour parameter value. * Provide the Enabled parameter.   Save the result to the $windowoptions variable.   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [Set-VBRJobSchedule](set-vbrjobschedule.md) cmdlet. Specify the following settings:  * Set the $job variable as the Job parameter value. * Provide the Periodicaly parameter. * Specify the FullPeriod parameter value. * Set the Hours option for the PeriodicallyKind parameter. * Set the $windowoptions as the PeriodicallySchedule parameter value. |

Related Commands

* [Set-VBRJobSchedule](set-vbrjobschedule.md)
* [Get-VBRJob](get-vbrjob.md)


