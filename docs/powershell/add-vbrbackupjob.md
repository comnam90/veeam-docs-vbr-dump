---
title: "Add-VBRBackupJob (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrbackupjob.html"
last_updated: "6/3/2024"
product_version: "13.0.1.1071"
---

# Add-VBRBackupJob (obsolete)


Short Description

Creates a new backup job.

|  |
| --- |
| Note |
| This cmdlet is obsolete. The cmdlet still works, but it is recommended to create a new backup job using the [Add-VBRViBackupJob](add-vbrvibackupjob.md) or [Add-VBRHvBackupJob](add-vbrhvbackupjob.md) cmdlets. |

Applies to

Platform: VMware

Syntax

|  |
| --- |
| Add-VBRBackupJob -Name <String> [-Type <String>] -Server <CHost> [-Folder <String>] [-FileName <String>] -Objects <String[]> [-Description <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet allows you to create a new backup job.

Note that when you create a backup job, you need to run it manually unless you enable a job schedule.

Run the [Start-VBRJob](start-vbrjob.md) cmdlet to start the created job.

Run the [Set-VBRJobSchedule](set-vbrjobschedule.md) cmdlet to set schedule for the job.

Parameters

| Parameter | Description | Required | Position | Accept | Accept Wildcard Characters |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the string with the name of the created backup job. | True | 1 | False | False |
| Type | Specifies the string with the type of the created backup job which defines how VM data is retrieved:   * VDDK – Virtual Disk Development Kit (VMware vStorage API) * VCB – VMware Consolidated Backup (legacy mode) * NET – Network backup (legacy mode). | False | 2 | False | False |
| Server | Specifies the host where the created backup should be stored. | True | 3 | False | False |
| Folder | Specifies the string with the path to the folder where the created backup should be stored. | False | 4 | False | False |
| FileName | Specifies the string with the file name for the created backup (by default, the backup file is given the same name as the VM). | False | Named | False | False |
| Objects | Specifies the string with the names of VMs that you want to back up. | True | Named | True (ByValue, ByProperty Name) | False |
| Description | Specifies the description of the new backup job. | False | Named | False | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Creating Backup Job

This command creates a backup job with the following parameters:

* Name of the backup job: jobName
* Data retrieval type: VDDK
* Variable which contains the target host DNS name or IP address: $server
* Path to the backup folder: C:\VmBackups
* VMs which should be backed up: vm1, vm2

|  |
| --- |
| Add-VBRBackupJob –Name “jobName”–Type VDDK –Server $server –Folder "C:\VmBackups" –Objects vm1,vm2 |

Related Commands

[Get-VBRServer](get-vbrserver.md)


