---
title: "Add-VBRViSureBackupJob (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrvisurebackupjob.html"
last_updated: "2/21/2024"
product_version: "13.0.1.1071"
---

# Add-VBRViSureBackupJob (obsolete)


Short Description

Creates a VMware SureBackup job.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Add-VBRSureBackupJob](add-vbrsurebackupjob.md) cmdlet instead. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRViSureBackupJob -VirtualLab <VBRVirtualLab> [-Name <string>] [-Description <string>] [-ApplicationGroup <VBRApplicationGroup>] [-KeepApplicationGroupRunning] [-LinkedJob <VBRSureBackupLinkedJob[]>] [-MaxConcurrentVMs <int>] [-VerificationOptions <VBRSureBackupJobVerificationOptions>] [-ScheduleOptions <VBRSureBackupJobScheduleOptions>] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet creates VMware SureBackup jobs.

Note that when you create a backup job, you need to run it manually unless you enable a job schedule.

Run the [Start-VBRSureBackupJob](start-vbrsurebackupjob.md) cmdlet to run the job manually.

Run the [New-VBRSureBackupJobScheduleOptions](new-vbrsurebackupjobscheduleoptions.md) to set schedule for the job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| VirtualLab | Specifies a virtual lab. The cmdlet will use this virtual lab to verify VMs. | Accepts the VBRVirtualLab object. To create this object, run the [Get-VBRVirtualLab](get-vbrvirtuallab.md) cmdlet. | True | Named | False |
| Name | Specifies a name for a SureBackup job. The cmdlet will create a SureBackup job with this name. | String | False | Named | False |
| Description | Specifies a description for a SureBackup job. The cmdlet will create a SureBackup job with this description. | String | False | Named | False |
| ApplicationGroup | Specifies an application group. Veeam Backup & Replication will use this application group to use for recovery verification. | Accepts the VBRApplicationGroup object. To create this object, run the [Get-VBRApplicationGroup](get-vbrapplicationgroup.md) cmdlet. | False | Named | False |
| KeepApplicationGroupRunning | Defines that VMs from an application group will run after the SureBackup job finishes.  If you provide this parameter, the application group will not be powered off when the SureBackup job finishes. Otherwise, the application group will be powered off. | SwitchParamter | False | Named | False |
| LinkedJob | Specifies a backup or replication job. The cmdlet will verify VMs that are added to this job with the SureBackup job. | Accepts the VBRSureBackupLinkedJob[] object. To create this object, run the [New-VBRSureBackupLinkedJob](new-vbrsurebackuplinkedjob.md) cmdlet. | False | Named | False |
| MaxConcurrentVMs | Specifies the maximum number of VMs that can be started at the same time. | Int32 | False | Named | False |
| VerificationOptions | Specifies additional settings for the SureBackup job. | Accepts the VBRSureBackupJobVerificationOptions object. To create this object, run the [New-VBRSureBackupJobVerificationOptions](new-vbrsurebackupjobverificationoptions.md) cmdlet. | False | Named | False |
| ScheduleOptions | Specifies schedule settings of a SureBackup job. Veeam Backup & Replication will run the job according to these settings. | Accepts the VBRSureBackupJobScheduleOptions object. To create this object, run the [New-VBRSureBackupJobScheduleOptions](new-vbrsurebackupjobscheduleoptions.md) cmdlet. | False | Named | False |
| Force | Defines that the cmdlet will not show any warnings. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRViSureBackupJob object that defines settings of SureBackup jobs.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding SureBackup Job

|  |  |
| --- | --- |
| This example shows how to create a SureBackup job.  |  | | --- | | $lab = Get-VBRVirtualLab -Name "Virtual Lab 2"  Add-VBRViSureBackupJob -VirtualLab $lab -Name "Verification Job01" -Description "SureBackup Job for DNS" |  Perform the following steps:   1. Run the [Get-VBRVirtualLab](get-vbrvirtuallab.md) cmdlet. Specify the Name parameter value. Save the result to the $lab variable. 2. Run the Add-VBRViSureBackupJob cmdlet. Specify the following settings:  * Set the $lab variable as the VirtualLab parameter value. * Specify the Name parameter value. * Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding SureBackup Job with Application Group

|  |  |
| --- | --- |
| This example shows how to create a SureBackup job that will use the Exchange Group 3 application group for recovery verification. Veeam Backup & Replication will keep VMs from an application group running after the SureBackup job finishes.  |  | | --- | | $lab = Get-VBRVirtualLab -Name "Virtual Lab 2"  $group = Get-VBRApplicationGroup -Name "Exchange Lab"  Add-VBRViSureBackupJob -VirtualLab $lab -ApplicationGroup $group -KeepApplicationGroupRunning |  Perform the following steps:   1. Run the [Get-VBRVirtualLab](get-vbrvirtuallab.md) cmdlet. Specify the Name parameter value. Save the result to the $lab variable. 2. Run the [Get-VBRApplicationGroup](get-vbrapplicationgroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 3. Run the Add-VBRViSureBackupJob cmdlet. Specify the following settings:  * Set the $lab variable as the VirtualLab parameter value. * Specify the $group variable as the ApplicationGroup parameter value. * Specify the KeepApplicationGroupRunning parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Adding SureBackup Job with Recovery Verification Options

|  |  |
| --- | --- |
| This example shows how to create a SureBackup job with recovery verification options.  |  | | --- | | $lab = Get-VBRVirtualLab -Name "Virtual Lab 2"  $options = New-VBRSureBackupJobVerificationOptions  Add-VBRViSureBackupJob -VirtualLab $lab -VerificationOptions $options |  Perform the following steps:   1. Run the [Get-VBRVirtualLab](get-vbrvirtuallab.md) cmdlet. Specify the Name parameter value. Save the result to the $lab variable. 2. Run the [New-VBRSureBackupJobVerificationOptions](new-vbrsurebackupjobverificationoptions.md) cmdlet. Save the result to the $options variable. 3. Run the Add-VBRViSureBackupJob cmdlet. Specify the following settings:  * Set the $lab variable as the VirtualLab parameter value. * Specify the $options variable as the VerificationOptions parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Adding SureBackup Job with Schedule Settings

|  |  |
| --- | --- |
| This example shows how to create a scheduled SureBackup job.  |  | | --- | | $lab = Get-VBRVirtualLab -Name "Virtual Lab 2"  $schedule = New-VBRSureBackupJobScheduleOptions  Add-VBRViSureBackupJob -VirtualLab $lab -ScheduleOptions $schedule |  Perform the following steps:   1. Run the [Get-VBRVirtualLab](get-vbrvirtuallab.md) cmdlet. Specify the Name parameter value. Save the result to the $lab variable. 2. Run the [New-VBRSureBackupJobScheduleOptions](new-vbrsurebackupjobscheduleoptions.md) cmdlet. Save the result to the $schedule variable. 3. Run the Add-VBRViSureBackupJob cmdlet. Set the $lab variable as the VirtualLab parameter value. Set the $schedule variable as the ScheduleOptions parameter value. |

Related Commands

* [Get-VBRVirtualLab](get-vbrvirtuallab.md)
* [Get-VBRApplicationGroup](get-vbrapplicationgroup.md)
* [New-VBRSureBackupJobVerificationOptions](new-vbrsurebackupjobverificationoptions.md)
* [New-VBRSureBackupJobScheduleOptions](new-vbrsurebackupjobscheduleoptions.md)


