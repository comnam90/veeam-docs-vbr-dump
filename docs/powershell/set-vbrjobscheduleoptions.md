---
title: "Set-VBRJobScheduleOptions (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrjobscheduleoptions.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Set-VBRJobScheduleOptions (obsolete)

In this article

Short Description

Applies modified job schedule settings to jobs.

|  |
| --- |
| Note |
| This cmdlet is obsolete. You can still run this cmdlet, but it is recommended to modify job schedule using the [Set-VBRJobSchedule](set-vbrjobschedule.md) cmdlet. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRJobScheduleOptions -Job <CBackupJob[]> -Options <ScheduleOptions>  [<CommonParameters>] |

Detailed Description

This cmdlet applies customized scheduling options to a selected backup, replication or copy job.

Run the [New-VBRJobScheduleOptions](new-vbrjobscheduleoptions.md) cmdlet to create the new schedule settings.

You can modify schedule of backup, replication or backup copy jobs.

Run the [Set-VSBJobScheduleOptions](set-vsbjobscheduleoptions.md) cmdlet to set scheduling options to SureBackup job.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameters values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of jobs. The cmdlet will apply schedule settings to these jobs. | Accepts the CBackupJob object. To create this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | True | 0 | True (ByProperty Name, ByValue) |
| Options | Specifies the schedule options you want to apply. | Accepts the VBRServerScheduleOptions object. To create this object, run the [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) cmdlet. | True | 1 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Scheduling Backup Job with Time Interval of 2 Hours

|  |  |
| --- | --- |
| This example shows how to schedule the backup job to run repeatedly throughout a day with the time interval of 2 hours.  |  | | --- | | $newschedule = New-VBRJobScheduleOptions  $newschedule.OptionsPeriodically.Enabled = $true  $newschedule.OptionsPeriodically.FullPeriod = 120  $newschedule.OptionsDaily.Enabled = $false  $job = Get-VBRJob -Name "Backup Job 1"  Set-VBRJobScheduleOptions -Job $job -Options $newschedule |  Perform the following steps:   1. Run the [New-VBRJobScheduleOptions](new-vbrjobscheduleoptions.md) cmdlet. Save the result to the $newschedule variable. 2. Provide $true value for the the OptionsPeriodically property of the $newschedule variable. 3. Specify the value for the OptionsPeriodically property in minutes. 4. Provide the $false value for the OptionsDaily property of the $newschedule variable. 5. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 6. Run the Set-VBRJobScheduleOptions cmdlet. Set the $job variable as the Job parameter value. Set the $newschedule variable as the Options parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Applying Customized Scheduling Options to Specific Jobs [Using Pipeline]

|  |  |
| --- | --- |
| This command applies the customized scheduling options to the jobs named DC Backup and DC File Copy.  |  | | --- | | $ScheduleOptions = New-VBRJobScheduleOptions  Get-VBRJob -Name "DC Backup", "DC File Copy" | Set-VBRJobScheduleOptions -Options $ScheduleOptions |  Perform the following steps:   1. Run the [New-VBRJobScheduleOptions](new-vbrjobscheduleoptions.md) cmdlet. Save the result to the $ScheduleOptions variable. 2. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. 3. Pipe the cmdlet output to the Set-VBRJobScheduleOptions cmdlet. Set the $ScheduleOptions variable as the Options parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Applying Customized Scheduling Options to Specific Job [Using Variable]

|  |  |
| --- | --- |
| This command applies the customized scheduling options to the job represented by the $job variable.  |  | | --- | | $job = Get-VBRJob  $ScheduleOptions = New-VBRJobScheduleOptions  Set-VBRJobScheduleOptions -Job $job -Options $ScheduleOptions |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Save the result to the $job variable. 2. Run the [New-VBRJobScheduleOptions](new-vbrjobscheduleoptions.md) cmdlet. Save the result to the $ScheduleOptions variable. 3. Run the Set-VBRJobScheduleOptions cmdlet. Set the $job variable as the Job parameter value. Set the $ScheduleOptions variable as the Options parameter value. |

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [New-VBRJobScheduleOptions](new-vbrjobscheduleoptions.md)

Page updated 3/11/2024

Page content applies to build 13.0.1.1071
