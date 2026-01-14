---
title: "Set-VBRSureBackupContentScanJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrsurebackupcontentscanjob.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Set-VBRSureBackupContentScanJob

In this article

Short Description

Modifies settings of a SureBackup job that runs in the backup content scan verification mode.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRSureBackupContentScanJob -Job <VBRSureBackupContentScanJob> [-Name <String>] [-Description <String>] [-LinkedJob <VBRSureBackupLinkedJob[]>] [-MaxConcurrentVMs <Int32>] [-ProcessRandomMachines] [-RandomMachinesMaxCount <Int32>] [-ScheduleOptions <VBRSureBackupJobScheduleOptions>] [-VerificationOptions <VBRSureBackupJobVerificationOptions>] [-EnableSchedule] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of a SureBackup job that runs in the backup content scan verification mode.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies a SureBackup job. The cmdlet will modify settings of this job. | Accepts the VBRSureBackupContentScanJob object. To create this object, run the [Get-VBRSureBackupJob](get-vbrsurebackupjob.md) cmdlet. | True | Named | True (ByValue, |
| Name | Specifies a name for a SureBackup job. The cmdlet will create a SureBackup job with this name. | String | False | Named | False |
| Description | Specifies a description for a SureBackup job. The cmdlet will create a SureBackup job with this description. | String | False | Named | False |
| LinkedJob | Specifies a backup or replication job. The cmdlet will verify VMs that are added to this job with the SureBackup job. | Accepts the VBRSureBackupLinkedJob[] object. To create this object, run the [New-VBRSureBackupLinkedJob](new-vbrsurebackuplinkedjob.md) cmdlet. | False | Named | False |
| MaxConcurrentVMs | Specifies the maximum number of VMs that can be started at the same time. | Int32 | False | Named | False |
| ProcessRandomMachines | Defines that the cmdlet will randomly test the specified number of machines from the linked job.  Use the RandomMachinesMaxCount parameter to specify the number of machines to randomly test. | SwitchParamter | False | Named | False |
| VerificationOptions | Specifies verification settings for a SureBackup job. | Accepts the VBRSureBackupJobVerificationOptions object. To create this object, run the [New-VBRSureBackupJobVerificationOptions](new-vbrsurebackupjobverificationoptions.md) cmdlet. | False | Named | False |
| ScheduleOptions | Specifies schedule settings of a SureBackup job. Veeam Backup & Replication will run the job according to these settings. | Accepts the VBRSureBackupJobScheduleOptions object. To create this object, run the [New-VBRSureBackupJobScheduleOptions](new-vbrsurebackupjobscheduleoptions.md) cmdlet. | False | Named | False |
| EnableSchedule | Defines that Veeam Backup & Replication will run the job according to schedule. | SwitchParamter |  |  |  |
| RandomMachinesMaxCount | Specifies the number of machines to randomly test during each run. The cmdlet will randomly test the specified number of machines from the linked job. | Int32 | False | Named | False |
| Force | Defines that the cmdlet will not show any warnings. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSureBackupContentScanJob object that defines settings of lite SureBackup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Name and Description for Backup Content Scan SureBackup Job

|  |  |
| --- | --- |
| This example shows how to modify name and description for the backup content scan SureBackup job named Exchange Job.  |  | | --- | | $surejob = Get-VBRSureBackupJob -Name "Exchange Job"  Set-VBRSureBackupContentScanJob -Job $surejob -Name "New Exchange Job" -Description "Job for DNS" |  Perform the following steps:   1. Run the [Get-VBRSureBackupJob](get-vbrsurebackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $surejob variable. 2. Run the Set-VBRSureBackupContentScanJob cmdlet. Set the $surejob variable as the Job parameter value. Specify the Name parameter value. Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Schedule Settings for Backup Content Scan SureBackup Job

|  |  |
| --- | --- |
| This example shows how to modify schedule settings for the backup content scan SureBackup job named Exchange Job.  |  | | --- | | $surejob = Get-VBRSureBackupJob -Name "Exchange Job"  $daily = New-VBRDailyOptions -DayOfWeek "Friday" -Period "23:00"  $schedule = New-VBRSureBackupJobScheduleOptions -Type "Daily" -DailyOptions $daily  Set-VBRSureBackupContentScanJob -Job $surejob -ScheduleOptions $schedule |  Perform the following steps:   1. Run the [Get-VBRSureBackupJob](get-vbrsurebackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $surejob variable. 2. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Specify the DayOfWeek and the Period parameter values. Save the result to the $daily variable. 3. Run the [New-VBRSureBackupJobScheduleOptions](new-vbrsurebackupjobscheduleoptions.md) cmdlet. Specify the Type parameter value. Set the $daily variable as the DailyOptions parameter value. Save the result to the $schedule variable. 4. Run the Set-VBRSureBackupContentScanJob cmdlet. Set the $surejob variable as the Job parameter value. Set the $schedule variable as the ScheduleOptions parameter value. |

Related Commands

* [New-VBRDailyOptions](new-vbrdailyoptions.md)
* [Get-VBRSureBackupJob](get-vbrsurebackupjob.md)
* [New-VBRSureBackupJobScheduleOptions](new-vbrsurebackupjobscheduleoptions.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
