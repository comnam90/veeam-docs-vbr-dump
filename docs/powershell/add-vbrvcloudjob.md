---
title: "Add-VBRvCloudJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrvcloudjob.html"
last_updated: "10/1/2025"
product_version: "13.0.1.1071"
---

# Add-VBRvCloudJob

In this article

Short Description

Creates a Cloud Director backup job.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRvCloudJob [-Name <String>] [-BackupRepository <CBackupRepository>] -Entity <IVcdItem[]> [-Description <String>] [-HighPriority] [-TargetBackup <CBackup>] [-EncryptionKey <PSCryptoKey>] [-KMSServer <VBRKMSServer>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new Cloud Director backup job.

You should always use Cloud Director backup jobs to back up VMs managed by Cloud Director. If you back up VMs managed by Cloud Director using a regular backup job, Veeam Backup & Replication will perform backup at the level of the underlying vCenter Server and will not capture vApp metadata. As a result, it will not let you restore a fully functioning VM to Cloud Director.

Note that when you create a backup job, you need to run it manually unless you enable a job schedule.

Run the [Start-VBRJob](start-vbrjob.md) cmdlet to start the created job.

Run the [Set-VBRJobSchedule](set-vbrjobschedule.md) cmdlet to set schedule for the job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Entity | Specifies the array of VMs. The cmdlet will add these VMs to the Cloud Director backup job. | Accepts the IVcdItem[] object. To get this object, run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. | True | Named | True |
| Name | Specifies the name you want to assign to the Cloud Director backup job. | String | False | Named | False |
| BackupRepository | Specifies the target backup repository.  Default: default backup repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| Description | Specifies the description of the new Cloud Director backup job. | String | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | SwitchParameter | False | Named | False |
| EncryptionKey | Specifies the encryption key that you want to use to encrypt the data. | Accepts the PSCryptoKey object. To create this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| KMSServer | Specifies KMS servers added to the Veeam Backup & Replication console. The cmdlet will decrypt data encrypted by this server. | Accepts the [VBRKMSServer](vbrkmsserver.md) object. To get this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

CBackupJob

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding Cloud Director Backup Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to create a new Cloud Director backup job.  |  | | --- | | $vm = Find-VBRvCloudEntity -Name "vCloud Server"  $brepository = Get-VBRBackupRepository -Name "Backups Vol2"  Add-VBRvCloudJob -Entity $vm -Name "vCD Backup Job" -BackupRepository $brepository -Description "Cloud Director Backup Job" |  Perform the following steps:   1. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Specify the Name parameter value. Save the result to the $vm variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $brepository variable. 3. Run the Add-VBRvCloudJob cmdlet. Specify the following settings:  * Set the $vm variable as the Entity parameter value. * Specify the Name parameter value. * Set the $brepository variable as the BackupRepository parameter value. * Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding Cloud Director Backup Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to create a new Cloud Director backup job. The target is the default backup repository.  |  | | --- | | Find-VBRvCloudEntity -Name "vCloud Server" | Add-VBRvCloudJob -Name "vCD Backup Job 2" -Description "Cloud Director Backup Job" |  Perform the following steps:   1. Run the [Find-VBRvCloudEntity](find-vbrvcloudentity.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Add-VBRvCloudJob cmdlet. Specify the Name and the Description parameter values. |

Related Commands

* [Find-VBRvCloudEntity](find-vbrvcloudentity.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)

Page updated 10/1/2025

Page content applies to build 13.0.1.1071
