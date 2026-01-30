---
title: "Set-VBRSureBackupJob"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrsurebackupjob.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Set-VBRSureBackupJob


Short Description

Modifies settings of SureBackup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRSureBackupJob -Job <VBRSureBackupJob> [-Name <String>] [-Description <String>] [-VirtualLab <VBRVirtualLab>] [-ApplicationGroup <VBRApplicationGroup>] [-KeepApplicationGroupRunning] [-LinkedJob <VBRSureBackupLinkedJob[]>] [-EnableLinkJob] [-MaxConcurrentVMs <Int32>] [-ProcessRandomMachines] [-VerificationOptions <VBRSureBackupJobVerificationOptions>] [-ScheduleOptions <VBRSureBackupJobScheduleOptions>] [-EnableSchedule] [-Force] [-RandomMachinesMaxCount <Int32>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of SureBackup jobs.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Job | Specifies a SureBackup job. The cmdlet will modify settings of this job. | Accepts the VBRSureBackupJob object. To create this object, run the [Get-VBRSureBackupJob](get-vbrsurebackupjob.md) cmdlet. | True | Named | True (ByValue, |
| Name | Specifies a name for a SureBackup job. The cmdlet will replace an existing name of the SureBackup job with this name. | String | False | Named | False |
| Description | Specifies a description for a SureBackup job. The cmdlet will replace an existing description of the SureBackup job with this description. | String | False | Named | False |
| VirtualLab | Specifies a virtual lab. The cmdlet will use this virtual lab to verify VMs. | Accepts the VBRVirtualLab object. To create this object, run the [Get-VBRVirtualLab](get-vbrvirtuallab.md) cmdlet. | False | Named | False |
| ApplicationGroup | Specifies an application group. Veeam Backup & Replication will use this application group to use for recovery verification. | Accepts the VBRApplicationGroup object. To create this object, run the [Get-VBRApplicationGroup](get-vbrapplicationgroup.md) cmdlet. | False | Named | False |
| KeepApplicationGroupRunning | Defines that VMs from an application group will run after the SureBackup job finishes.  If you provide this parameter, the application group will not be powered off when the SureBackup job finishes. Otherwise, the application group will be powered off. | SwitchParamter | False | Named | False |
| LinkedJob | Specifies a backup or replication job. The cmdlet will verify VMs that are added to this job with the SureBackup job. | Accepts the VBRSureBackupLinkedJob[] object. To create this object, run the [New-VBRSureBackupLinkedJob](new-vbrsurebackuplinkedjob.md) cmdlet. | False | Named | False |
| EnableLinkJob | Defines that the cmdlet will link jobs with VMs that you want to verify with the SureBackup job.  If you provide this parameter, the Veeam Backup & Replication will verify VMs that are added to specified jobs with the SureBackup job. Otherwise, Veeam Backup & Replication will verify VMs from the application group only.  Provide the LinkedJob parameter to specify jobs that you want to link to a SureBackup job. | SwitchParamter | False | Named | False |
| MaxConcurrentVMs | Specifies the maximum number of VMs that can be started at the same time. | Int32 | False | Named | False |
| VerificationOptions | Specifies recovery verification options for every VM from the jobs linked to the SureBackup job. | Accepts the VBRSureBackupJobVerificationOptions object. To create this object, run the [New-VBRSureBackupJobVerificationOptions](new-vbrsurebackupjobverificationoptions.md) cmdlet. | False | Named | False |
| ScheduleOptions | Specifies schedule settings of a SureBackup job. Veeam Backup & Replication will run the job according to these settings. | Accepts the VBRSureBackupJobScheduleOptions object. To create this object, run the [New-VBRSureBackupJobScheduleOptions](new-vbrsurebackupjobscheduleoptions.md) cmdlet. | False | Named | False |
| EnableSchedule | Defines that the cmdlet will enable a schedule for a SureBackup job.  If you provide this option, the SureBackup job will run according the specified schedule. Otherwise, you must start the job manually.  Provide the ScheduleOptions parameter to specify the schedule options. | SwitchParamter | False | Named | False |
| RandomMachinesMaxCount | Specifies the number of machines to randomly test during each run. The cmdlet will randomly test the specified number of machines from the linked job. | Int32 | False | Named | False |
| ProcessRandomMachines | Defines that the cmdlet will randomly test the specified number of machines from the linked job.  Use the RandomMachinesMaxCount parameter to specify the number of machines to randomly test. | SwitchParamter | False | Named | False |
| Force | Defines that the cmdlet will not show any warnings. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSureBackupJob object that defines settings of SureBackup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Application Group of SureBackup Job

|  |  |
| --- | --- |
| This example shows how to modify an application group for the SureBackup job named Exchange Job.  |  | | --- | | $surejob = Get-VBRSureBackupJob -Name "Exchange Job"  $appgroup = Get-VBRApplicationGroup -Name "Exchange Application Group"  Set-VBRSureBackupJob -Job $surejob -ApplicationGroup $appgroup |  Perform the following steps:   1. Run the [Get-VBRSureBackupJob](get-vbrsurebackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $surejob variable. 2. Run the [Get-VBRApplicationGroup](get-vbrapplicationgroup.md) cmdlet. Specify the Name parameter value. Save the result to the $appgroup variable. 3. Run the Set-VBRSureBackupJob cmdlet. Set the $surejob variable as the Job parameter value. Set the $appgroup variable as the ApplicationGroup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Virtual Lab of SureBackup Job

|  |  |
| --- | --- |
| This example shows how to modify a virtual lab for the SureBackup job named Exchange Job.  |  | | --- | | $surejob = Get-VBRSureBackupJob -Name "Exchange Job"  $lab = Get-VBRVirtualLab -Name "Exchange Lab"  Set-VBRSureBackupJob -Job $surejob -VirtualLab $lab |  Perform the following steps:   1. Run the [Get-VBRSureBackupJob](get-vbrsurebackupjob.md) cmdlet. Specify the Name parameter value. Save the result to the $surejob variable. 2. Run the [Get-VBRVirtualLab](get-vbrvirtuallab.md) cmdlet. Specify the Name parameter value. Save the result to the $lab variable. 3. Run the Set-VBRSureBackupJob cmdlet. Set the $surejob variable as the Job parameter value. Set the $lab variable as the VirtualLab parameter value. |

Related Commands

* [Get-VBRVirtualLab](get-vbrvirtuallab.md)
* [Get-VBRSureBackupJob](get-vbrsurebackupjob.md)


