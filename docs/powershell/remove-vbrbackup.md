---
title: "Remove-VBRBackup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrbackup.html"
last_updated: "4/1/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRBackup


Short Description

Removes selected backups.

|  |
| --- |
| Note |
| If the four-eyes authorization is enabled, you cannot run this cmdlet. For more information, see the [Four-Eyes Authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) section in the User Guide for VMware vSphere. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Remove selected backups from the database.

|  |
| --- |
| Remove-VBRBackup -Backup <CBackup[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Remove selected backups from the disk.

|  |
| --- |
| Remove-VBRBackup -Backup <CBackup[]> -FromDisk [-RunAsync] [-IncludeGFS] [-FromDBIfSPUnavailable] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes selected backups created by all types of jobs: backup jobs, backup copy jobs, Cloud Director jobs and Veeam Agent for Microsoft Windows backup jobs. When you remove backups, you can use the following options:

* Remove from the database. When you remove a backup from the database, you remove records about the backup from the Veeam configuration database. The backup files remain in the repository. You can import these backups later with the [Import-VBRBackup](import-vbrbackup.md) cmdlet.

|  |
| --- |
| Note |
| Cloud Connect backups cannot be removed with this option. To remove a Cloud Connect backup from the configuration, contact Veeam Support. |

* Remove from the disk. With this option, the backup is removed from the database and from the disk. This removal is complete and non-reversible.

|  |
| --- |
| Important |
| You must use this option if you want to remove backups from archive extents and capacity extents. |

This cmdlet removes all restore points associated with backups of all VMs processed by the job. You should remove backups carefully considering the subsequent backup jobs that may fail to produce a valid backup. To remove backups of individual VMs, run the [Remove-VBRRestorePoint](remove-vbrrestorepoint.md) cmdlet.

To remove a replicated VM, run the [Remove-VBRReplica](remove-vbrreplica.md) cmdlet.

To remove a backup job, run the [Remove-VBRJob](remove-vbrjob.md) cmdlet.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies the array of backups you want to remove. | Accepts the CBackup[] object. To get this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet.  [For backups from archive extents and capacity extents] Accepts the [VBRSOBRObjectStorageBackup](vbrsobrobjectstoragebackup.md) object. To get this object, run the [Get-VBRSOBRObjectStorageBackup](get-vbrsobrobjectstoragebackup.md) cmdlet. | True | 0 | True (ByValue, ByProperty Name) |
| IncludeGFS | Defines that the cmdlet will remove backups with GFS flags (weekly, monthly and yearly). | SwitchParameter | False | Named | False |
| FromDBIfSPUnavailable | Defines that the cmdlet will remove backups from a database if a cloud provider is not available. | SwitchParameter | False | Named | False |
| FromDisk | Defines that the cmdlet will delete backups from disk. If you do not provide this parameter, the cmdlet will delete only the information about the backups.  Note: You must provide this parameter to remove backups from archive extents and capacity extents. | SwitchParameter | True | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwichParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Specific Backups from Database [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to remove the backups named Backup Job 01 and Backup Job 02 from the database.  |  | | --- | | Get-VBRBackup -Name "Backup Job 01", "Backup Job 02" | Remove-VBRBackup |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Remove-VBRBackup cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Backups from Disk with Specified Names [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to remove backups ending with 2012 characters from the disk.  |  | | --- | | Get-VBRBackup -Name \*2012 | Remove-VBRBackup -FromDisk |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Remove-VBRBackup cmdlet. Provide the FromDisk parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Removing Backup from Disk [Using Variable]

|  |  |
| --- | --- |
| This example shows how to delete backups from the disk.  |  | | --- | | $backup = Get-VBRBackup -Name "Backups"  Remove-VBRBackup -Backup $backup -FromDisk |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the Remove-VBRBackup cmdlet. Set the $backup variable as the Backup parameter value. Provide the FromDisk parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Removing Backups from Capacity Extents

|  |  |
| --- | --- |
| This example shows how to delete backups from capacity extents of a scale-out backup repository.  |  | | --- | | $backup = Get-VBRSOBRObjectStorageBackup -CapacityTier  Remove-VBRBackup -Backup $backup -FromDisk |  Perform the following steps:   1. Run the [Get-VBRSOBRObjectStorageBackup](get-vbrsobrobjectstoragebackup.md) cmdlet. Provide the CapacityTier parameter value. Save the result to the $backup variable. 2. Run the Remove-VBRBackup cmdlet. Set the $backup variable as the Backup parameter value. Provide the FromDisk parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 5. Removing Backups from Archive Extents

|  |  |
| --- | --- |
| This example shows how to delete backups from archive extents of a scale-out backup repository.  |  | | --- | | $backup = Get-VBRSOBRObjectStorageBackup -ArchiveTier  Remove-VBRBackup -Backup $backup -FromDisk |  Perform the following steps:   1. Run the [Get-VBRSOBRObjectStorageBackup](get-vbrsobrobjectstoragebackup.md) cmdlet. Provide the ArchiveTier parameter value. Save the result to the $backup variable.  1. Run the Remove-VBRBackup cmdlet. Set the $backup variable as the Backup parameter value. Provide the FromDisk parameter. |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRSOBRObjectStorageBackup](get-vbrsobrobjectstoragebackup.md)


