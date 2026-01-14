---
title: "Add-VBRSureBackupContentScanJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrsurebackupcontentscanjob.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Add-VBRSureBackupContentScanJob

In this article

Short Description

Creates a backup content scan SureBackup job.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRSureBackupContentScanJob -LinkedJob <VBRSureBackupLinkedJob[]> -VerificationOptions <VBRSureBackupJobVerificationOptions> [-Name <String>] [-Description <String>] [-MaxConcurrentVMs <Int32>] [-ProcessRandomMachines] [-ScheduleOptions <VBRSureBackupJobScheduleOptions>] [-Force] [-RandomMachinesMaxCount <Int32>]  [<CommonParameters>] |

Detailed Description

This cmdlet createsa SureBackup job that runs in the backup content scan verification mode. This SureBackup job performs only backup integrity check and its content analysis to detect traces of malware or any other unwanted or sensitive data. These tests do no require setting up a virtual lab or an application group.

Note that when you create a backup job, you need to run it manually unless you enable a job schedule.

Run the [Start-VBRSureBackupJob](start-vbrsurebackupjob.md) cmdlet to run the job manually.

Run the [New-VBRSureBackupJobScheduleOptions](new-vbrsurebackupjobscheduleoptions.md) to set schedule for the job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| LinkedJob | Specifies a backup or replication job. The cmdlet will verify VMs that are added to this job with the lite SureBackup job. | Accepts the VBRSureBackupLinkedJob[] object. To create this object, run the [New-VBRSureBackupLinkedJob](new-vbrsurebackuplinkedjob.md) cmdlet. | True | Named | False |
| VerificationOptions | Specifies verification settings for a SureBackup job. | Accepts the VBRSureBackupJobVerificationOptions object. To create this object, run the [New-VBRSureBackupJobVerificationOptions](new-vbrsurebackupjobverificationoptions.md) cmdlet. | True | Named | False |
| Name | Specifies a name for a SureBackup job. The cmdlet will create a SureBackup job with this name. | String | False | Named | False |
| Description | Specifies a description for a SureBackup job. The cmdlet will create a SureBackup job with this description. | String | False | Named | False |
| MaxConcurrentVMs | Specifies the maximum number of VMs that can be started at the same time. | Int32 | False | Named | False |
| ProcessRandomMachines | Defines that the cmdlet will randomly test the specified number of machines from the linked job.  Use the RandomMachinesMaxCount parameter to specify the number of machines to randomly test. | SwitchParamter | False | Named | False |
| ScheduleOptions | Specifies schedule settings of a SureBackup job. Veeam Backup & Replication will run the job according to these settings. | Accepts the VBRSureBackupJobScheduleOptions object. To create this object, run the [New-VBRSureBackupJobScheduleOptions](new-vbrsurebackupjobscheduleoptions.md) cmdlet. | False | Named | False |
| RandomMachinesMaxCount | Specifies the number of machines to randomly test during each run. The cmdlet will randomly test the specified number of machines from the linked job. | Int32 | False | Named | False |
| Force | Defines that the cmdlet will not show any warnings. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSureBackupContentScanJob object that defines settings of lite SureBackup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Backup Content Scan SureBackup Job

|  |  |
| --- | --- |
| This example shows how to create a backup content scan SureBackup job which will randomly scan 5 machines from the linked job named Exchange Job. Veeam Backup & Replication will scan these machines with antivirus software and the YARA rule.  |  | | --- | | $job = Get-VBRJob -Name "Exchange Job"  $linkedjob = New-VBRSureBackupLinkedJob -Job $job  $verification = New-VBRSureBackupJobVerificationOptions -EnableMalwareScan -EnableEntireImageScan -EnableYARAScan -YARAScanRule "Rule.yara"  Add-VBRSureBackupContentScanJob -LinkedJob $linkedjob -Name "Lite Verification Job" -VerificationOptions $verification -ProcessRandomMachines -RandomMachinesMaxCount "5" -Description "SureBackup Job for DNS" |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [New-VBRSureBackupLinkedJob](new-vbrsurebackuplinkedjob.md) cmdlet. Set the $job variable as the Job parameter value. Save the result to the $linkedjob variable. 3. Run the [New-VBRSureBackupJobVerificationOptions](new-vbrsurebackupjobverificationoptions.md) cmdlet. Provide the EnableMalwareScan, the EnableEntireImageScan and the EnableYARAScan parameters. Specify the YARAScanRule parameter value. Save the result to the $verification variable. 4. Run the Add-VBRSureBackupContentScanJob cmdlet. Specify the following settings:  * Set the $linkedjob variable as the LinkedJob parameter value. * Specify the Name parameter value. * Set the $verification variable as the VerificationOptions parameter value. * Provide the ProcessRandomMachines parameter. * Specify the RandomMachinesMaxCount parameter value. * Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Backup Content Scan SureBackup Job with Schedule Settings

|  |  |
| --- | --- |
| This example shows how to create a scheduled lite SureBackup job.  |  | | --- | | $job = Get-VBRJob -Name "Exchange Job"  $linkedjob = New-VBRSureBackupLinkedJob -Job $job  $verification = New-VBRSureBackupJobVerificationOptions -EnableMalwareScan -EnableEntireImageScan -EnableYARAScan -YARAScanRule "Rule.yara"  $daily = New-VBRDailyOptions -DayOfWeek "Friday" -Period "23:00"  $schedule = New-VBRSureBackupJobScheduleOptions -Type "Daily" -DailyOptions $daily  Add-VBRSureBackupContentScanJob -LinkedJob $linkedjob -VerificationOptions $verification -Name "Lite Verification Job" -ScheduleOptions $schedule -Description "SureBackup Job for DNS" |  Perform the following steps:   1. Run the [Get-VBRJob](get-vbrjob.md) cmdlet. Specify the Name parameter value. Save the result to the $job variable. 2. Run the [New-VBRSureBackupLinkedJob](new-vbrsurebackuplinkedjob.md) cmdlet. Set the $job variable as the Job parameter value. Save the result to the $linkedjob variable. 3. Run the [New-VBRSureBackupJobVerificationOptions](new-vbrsurebackupjobverificationoptions.md) cmdlet. Provide the EnableMalwareScan, the EnableEntireImageScan and the EnableYARAScan parameters. Specify the YARAScanRule parameter value. Save the result to the $verification variable. 4. Run the [New-VBRDailyOptions](new-vbrdailyoptions.md) cmdlet. Specify the DayOfWeek parameter and the Period parameter values. Save the result to the $daily variable. 5. Run the [New-VBRSureBackupJobScheduleOptions](new-vbrsurebackupjobscheduleoptions.md) cmdlet. Specify the Type parameter value. Set the $daily variable as the DailyOptions parameter value. Save the result to the $schedule variable. 6. Run the Add-VBRSureBackupContentScanJob cmdlet. Specify the following settings:  * Set the $linkedjob variable as the LinkedJob parameter value.  * Set the $verification variable as the VerificationOptions parameter value.  * Specify the Name parameter value. * Set the $schedule variable as the ScheduleOptions parameter value. * Specify the Description parameter value. |

Related Commands

* [Get-VBRJob](get-vbrjob.md)
* [New-VBRSureBackupLinkedJob](new-vbrsurebackuplinkedjob.md)
* [New-VBRSureBackupJobVerificationOptions](new-vbrsurebackupjobverificationoptions.md)
* [New-VBRDailyOptions](new-vbrdailyoptions.md)
* [New-VBRSureBackupJobScheduleOptions](new-vbrsurebackupjobscheduleoptions.md)

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
