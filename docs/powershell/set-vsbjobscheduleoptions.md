---
title: "Set-VSBJobScheduleOptions (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vsbjobscheduleoptions.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Set-VSBJobScheduleOptions (obsolete)


Short Description

Applies customized job scheduling options to a selected SureBackup job.

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
| Set-VSBJobScheduleOptions -Job <CSbJob> -Options <ScheduleOptions> [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet applies customized scheduling options to a selected SureBackup job.

To customize the scheduling options you need to first run the [New-VBRJobScheduleOptions](new-vbrjobscheduleoptions.md) cmdlet. The [New-VBRJobScheduleOptions](new-vbrjobscheduleoptions.md) returns the ScheduleOptions object containing the set of default scheduling options. You can customize any of these options and apply further to any kind of jobs.

Run the [Set-VBRJobScheduleOptions](set-vbrjobscheduleoptions.md) cmdlet to set scheduling options of backup, replication or copy job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies the array of the SureBackup jobs. The cmdlet will apply the schedule settings to these jobs. | Accepts the CSbJob object. To get this object, run the [Get-VSBJob](get-vsbjob.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |
| Options | Specifies the SureBackup job schedule options you want to apply. | Accepts the ScheduleOptions object. To get this object, run the [New-VBRJobScheduleOptions](new-vbrjobscheduleoptions.md) cmdlet. | True | 2 | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Applying Scheduling Options to SureBackup Jobs [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to apply the customized scheduling options to the SharePoint SureJob and MailServer SureJob SureBackup jobs.  |  | | --- | | $ScheduleOptions = New-VBRJobScheduleOptions  $ScheduleOptions.OptionsPeriodically.Enabled = $true  $ScheduleOptions.OptionsPeriodically.FullPeriod = 120  Get-VSBJob -Name "SharePoint SureJob", "MailServer SureJob" | Set-VSBJobScheduleOptions -Options $ScheduleOptions |  Perform the following steps:   1. Run the [New-VBRJobScheduleOptions](new-vbrjobscheduleoptions.md) cmdlet. Save the result to the $ScheduleOptions variable. 2. Provide the $true value for the OptionsPeriodically property of the $ScheduleOptions variable. 3. Specify the value for the OptionsPeriodically property in minutes. 4. Run the [Get-VSBJob](get-vsbjob.md) cmdlet. Specify the Name parameter value. 5. Pipe the cmdlet output to the Set-VSBJobScheduleOptions cmdlet. Set the $ScheduleOptions variable as the Options parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Applying Scheduling Options to SureBackup Jobs [Using Variable]

|  |  |
| --- | --- |
| This example shows how to apply the customized scheduling options to the SharePoint SureJob and MailServer SureJob SureBackup jobs.  |  | | --- | | $ScheduleOptions = New-VBRJobScheduleOptions  $ScheduleOptions.OptionsPeriodically.Enabled = $true  $ScheduleOptions.OptionsPeriodically.FullPeriod = 120  $SureJob = Get-VSBJob -Name "SharePoint SureJob", "MailServer SureJob"  Set-VSBJobScheduleOptions -Job $SureJob -Options $ScheduleOptions |  Perform the following steps:   1. Run the [New-VBRJobScheduleOptions](new-vbrjobscheduleoptions.md) cmdlet. Save the result to the $ScheduleOptions variable. 2. Provide the $true value for the OptionsPeriodically property of the $ScheduleOptions variable. 3. Specify the value for the OptionsPeriodically property in minutes. 4. Run the [Get-VSBJob](get-vsbjob.md) cmdlet. Specify the Name parameter value. Save the result to the $SureJob variable. 5. Run the Set-VSBJobScheduleOptions cmdlet. Set the $SureJob variable as the Job parameter value. Set the $ScheduleOptions variable as the Options parameter value. |

Related Commands

* [Get-VSBJob](get-vsbjob.md)
* [New-VBRJobScheduleOptions](new-vbrjobscheduleoptions.md)


