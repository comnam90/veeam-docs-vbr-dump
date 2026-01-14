---
title: "Add-VBRViBackupJob"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrvibackupjob.html"
last_updated: "12/16/2025"
product_version: "13.0.1.1071"
---

# Add-VBRViBackupJob

In this article

Short Description

Creates VMware backup jobs.

Applies to

Platform: VMware

For Hyper-V, run the [Add-VBRHvBackupJob](add-vbrhvbackupjob.md) cmdlet.

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRViBackupJob [-Name <string>] [-BackupRepository <CBackupRepository>] [-BackupLogsRepository <CBackupRepository>] -Entity <IViItem[]> [-Description <string>] [-Force] [-HighPriority] [-Multitag] [-EncryptionKey <PSCryptoKey>] [-KMSServer <VBRKMSServer>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a VMware backup job.

Note that when you create a backup job, you need to run it manually unless you enable a job schedule.

Run the [Start-VBRJob](start-vbrjob.md) cmdlet to run the job manually.

Run the [Set-VBRJobSchedule](set-vbrjobschedule.md) cmdlet to set schedule for the job.

|  |
| --- |
| Note |
| The cmdlet will not run if the geographic location of the VMs added to the job and the job target repository location do not match. If you still want to run the cmdlet, use the Force parameter. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name you want to assign to the backup job. | String | False | Named | False |
| BackupRepository | Specifies the backup repository where the created backup will be stored.  Default: default backup repository. | Accepts the CBackupRepository object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | False |
| Entity | Specifies the array of VMware VMs you want to add to the job. | Accepts the IViItem[] object. To get this object, run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. | True | Named | True (ByProperty Name, ByValue) |
| Description | Specifies the description of the backup job. | String | False | Named | False |
| Force | Defines that the cmdlet will create a backup job even if the geographic location of the VMs added to the job and the target backup repository location do not match. | SwitchParameter | False | Named | False |
| HighPriority | Defines that Veeam Backup & Replication will prioritize this job higher than other similar jobs and will allocate resources to it in the first place. | SwitchParameter | False | Named | False |
| Multitag | Defines that the cmdlet will add tags to an existing job. | SwitchParameter | False | Named | False |
| EncryptionKey | Specifies the encryption key that you want to use to encrypt the data. | Accepts the PSCryptoKey object. To get this object, run the [Get-VBREncryptionKey](get-vbrencryptionkey.md) cmdlet. | False | Named | False |
| KMSServer | Specifies KMS servers added to the Veeam Backup & Replication console. The cmdlet will decrypt data encrypted by this server. | Accepts the [VBRKMSServer](vbrkmsserver.md) object. To get this object, run the [Get-VBRKMSServer](get-vbrkmsserver.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Backup Job [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to create a backup job named Exchange Backup.  |  | | --- | | $Repository = Get-VBRBackupRepository -Name "Backup Repository"  Find-VBRViEntity -Name Exchange\* | Add-VBRViBackupJob -Name "Exchange Backup" -BackupRepository $Repository -Description "VMware Exchange Backup" |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $Repository variable. 2. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. 3. Pipe the cmdlet output to the Add-VBRViBackupJob cmdlet. Specify the following settings:  * Specify the Name parameter value. * Set the $Repository variable as the BackupRepository parameter value. * Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Backup Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to create a backup job for the VM represented by the $Vm variable.  |  | | --- | | $Repository = Get-VBRBackupRepository -Name "Backup Repository"  $Vm = Find-VBRViEntity -Name "VM01"  Add-VBRViBackupJob -BackupRepository $Repository -Entity $Vm |  Perform the following steps:   1. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save the result to the $Repository variable. 2. Run the [Find-VBRViEntity](find-vbrvientity.md) cmdlet. Specify the Name parameter value. Save the result to the $Vm variable. 3. Run the Add-VBRViBackupJob cmdlet. Set the $Repository variable as the BackupRepository parameter value. Set the $Vm variable as the Entity parameter value. |

Related Commands

* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Find-VBRViEntity](find-vbrvientity.md)

Page updated 12/16/2025

Page content applies to build 13.0.1.1071
