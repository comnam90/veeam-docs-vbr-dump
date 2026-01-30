---
title: "New-VBRJobScheduleOptions (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrjobscheduleoptions.html"
last_updated: "3/6/2024"
product_version: "13.0.1.1071"
---

# New-VBRJobScheduleOptions (obsolete)


Short Description

Creates new job schedule options.

|  |
| --- |
| Note |
| This cmdlet is obsolete. You can still run this cmdlet but, depending on the job type, it is recommended to run one of the following cmdlets:   * The [New-VBRServerScheduleOptions](new-vbrserverscheduleoptions.md) cmdlet to define schedule settings for backup jobs. * The [New-VBRWindowsWorkstationScheduleOptions](new-vbrwindowsworkstationscheduleoptions.md) cmdlet to create a job schedule for Windows workstations. * The [New-VBRLinuxScheduleOptions](new-vbrlinuxscheduleoptions.md) cmdlet to create a job schedule for Linux computers. * The [New-VBRMacScheduleOptions](new-vbrmacscheduleoptions.md) cmdlet to create a job schedule for macOS computers. * The [Set-VBRJobSchedule](set-vbrjobschedule.md) cmdlet to modify a job schedule. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRJobScheduleOptions  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRJobScheduleOptions object. This object contains default job scheduling settings. You can edit any setting that you want to apply to a job.

Run the [Set-VBRJobScheduleOptions](set-vbrjobscheduleoptions.md) cmdlet to apply the schedule to a job.

You can set schedule for backup, replication or copy jobs.

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRJobScheduleOptions object that contains default job scheduling settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Schedule Settings

|  |  |
| --- | --- |
| This command defines default schedule settings for a job. Save the result to the $newschedule variable for later use.  |  | | --- | | $newschedule = New-VBRJobScheduleOptions | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Scheduling Job with Time Interval of 2 Hours

|  |  |
| --- | --- |
| This example shows how to define schedule settings for a job. The job will run with the following schedule settings:   * The job will run repeatedly during a day. * The job will run every 120 minutes.   |  | | --- | | $newschedule = New-VBRJobScheduleOptions  $newschedule.OptionsPeriodically.Enabled = $true  $newschedule.OptionsPeriodically.FullPeriod = 120  $newschedule.OptionsDaily.Enabled = $false |  Perform the following steps:   1. Run the New-VBRJobScheduleOptions cmdlet. Save the result to the $newschedule variable. 2. Provide the $true value for the OptionsPeriodically property of the $newschedule variable. 3. Specify the value for the OptionsPeriodically property in minutes. 4. Provide the $false value for the OptionsDaily property of the $newschedule variable to disable the daily schedule option. |


