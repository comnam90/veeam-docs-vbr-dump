---
title: "Add-VBRTapeVMJob (obsolete)"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrtapevmjob.html"
last_updated: "2/21/2024"
product_version: "13.0.1.1071"
---

# Add-VBRTapeVMJob (obsolete)

In this article

Short Description

Creates a new backup to tape copy job.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet still works, but it is recommended to create backup to tape copy jobs using the [Add-VBRBackupToTapeJob](add-vbrbackuptotapejob.md) cmdlet. |

Applies to

Platform: VMware, Hyper-V

Syntax

|  |
| --- |
| Add-VBRTapeVMJob [-Name <String>] [-Repository <CBackupRepository[]>] [-BackupJob <CBackupJob[]>] -MediaPool <MediaPool> [-MediaPoolIncremental <MediaPool>] [-DisableIncremental] [-HardwareCompression] [-Description <String>] [-WarningAction <ActionPreference>] [-WarningVariable <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a new job that copies VM backups to tape.

To be able to create a backup to tape copy job, you need to have existing backups available.

You can copy VM backups in two ways:

* From backup jobs: the tape job looks for backup files that have been produced by the specified backup job from the moment of the last tape job run.
* From backup repository: the tape job looks for all VM backups that have written to the specified backup repository from the moment of the last tape job run.

Note that when you create a copy job, you need to run it manually.

Run the [Start-VBRJob](start-vbrjob.md) cmdlet to start the created job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the name you want to assign to the VM to tape copy job. | String | False | Named | False |
| Repository | Specifies a source backup repository you want to use as the source for the VM backups.  You can assign multiple backup repositories to this object. | Accepts the CBackupRepository[] object. To get this object, run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| BackupJob | Specifies the backup job you want to use as the source for the VM backups.  You can assign multiple backup jobs to this object. | Accepts the CBackupJob[] object. To get this object, run the [Get-VBRJob](get-vbrjob.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |
| MediaPool | Specifies the target media pool you want to use for full backups.  You can input string up to 255 symbols. | Accepts the MediaPool object. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | True | Named | False |
| MediaPool Incremental | Specifies the target media pool you want to use for incremental backups. | Accepts the MediaPool object. To get this object, run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. | False | Named | False |
| Disable Incremental | If set, the tape job will copy only the full backup files. Otherwise, the incremental backups will be written to the media pool set in the MediaPoolIncremental.  Note: Set this parameter in case you do not want to store the incremental backups on tape. If it is not set, the incremental backups will be written to the media pool you set for the full backups. | SwitchParameter | False | Named | False |
| Hardware Compression | Enables hardware compression option.  Note: If you plan to use hardware compression when recording backups to tape, consider that although it decreases traffic, this option affects performance. | SwitchParameter | False | Named | False |
| Description | Specifies the description of the new VM to tape copy job. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Backup to Tape Copy Job

|  |  |
| --- | --- |
| This example shows how to create the CRM Backup Copy to Tape job copying files from the CRM Backup backup job to tape.  |  | | --- | | $full = Get-VBRTapeMediaPool -Name "File Backup Media Pool Full"  $increment = Get-VBRTapeMediaPool -Name "File Backup Media Pool Incremental"  Get-VBRJob -Name "CRM Backup" | Add-VBRTapeVMJob -Name "CRM Backup Copy to Tape" -MediaPool $full -MediaPoolIncremental $increment -Description "CRM Backup Copy to Tape" |  Perform the following steps:   1. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save it to the $full variable. 2. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save it to the $increment variable. 3. Run the Get-VBRJob cmdlet. Specify the Name parameter value. 4. Pipe the cmdlet output to the Add-VBRTapeVMJob cmdlet. Specify the following settings:  * Specify the Name parameter value. * Set the $full variable as the MediaPool parameter value. * Set the $increment variable as the MediaPoolIncremental parameter value. * Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Backup Repository to Tape Copy Job

|  |  |
| --- | --- |
| This example shows how to create the Local Backup Copy to Tape job copying files from the Local Repository 01 backup repository to tape.  |  | | --- | | $full = Get-VBRTapeMediaPool -Name "File Backup Media Pool Full"  Get-VBRBackupRepository -Name "Local Repository 01" | Add-VBRTapeVMJob -Name "Local Backup Copy to Tape" - MediaPool $full -DisableIncremental -HardwareCompression |  Perform the following steps:   1. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save it to the $full variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. 3. Pipe the cmdlet output to the Add-VBRTapeVMJob cmdlet. Specify the following settings:  * Specify the Name parameter value. * Set the $full variable as the MediaPool parameter value. * Provide the DisableIncremental parameter. * Provide the HardwareCompression parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Creating Backup Repository to Tape Copy Job [Using Variable]

|  |  |
| --- | --- |
| This example shows how to create the Local Backup Copy to Tape job copying files from the Local Repository 01 backup repository to tape.  |  | | --- | | $full = Get-VBRTapeMediaPool -Name "File Backup Media Pool Full"  $repository = Get-VBRBackupRepository -Name "Local Repository 01"  Add-VBRTapeVMJob -Name "Local Backup Copy to Tape" -Repository $repository -MediaPool $full -DisableIncremental |  Perform the following steps:   1. Run the [Get-VBRTapeMediaPool](get-vbrtapemediapool.md) cmdlet. Specify the Name parameter value. Save it to the $full variable. 2. Run the [Get-VBRBackupRepository](get-vbrbackuprepository.md) cmdlet. Specify the Name parameter value. Save it to the $repository variable. 3. Run the Add-VBRTapeVMJob cmdlet. Specify the following settings:  * Specify the Name parameter value. * Set the $repository variable as the Repository parameter value. * Set the $full variable as the MediaPool parameter value. * Provide the DisableIncremental parameter. |

Related Commands

* [Get-VBRTapeMediaPool](get-vbrtapemediapool.md)
* [Get-VBRBackupRepository](get-vbrbackuprepository.md)
* [Get-VBRJob](get-vbrjob.md)

Page updated 2/21/2024

Page content applies to build 13.0.1.1071
