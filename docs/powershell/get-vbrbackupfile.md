---
title: "Get-VBRBackupFile"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrbackupfile.html"
last_updated: "2/12/2024"
product_version: "13.0.1.1071"
---

# Get-VBRBackupFile


Short Description

Returns backup files.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus

Syntax

This cmdlet provides the following parameter sets that allow you to:

* Get backup files from the specified backup.

|  |
| --- |
| Get-VBRBackupFile -Backup <CBackup> [-Path <String[]>]  [<CommonParameters>] |

* Get backup files with the ID option.

|  |
| --- |
| Get-VBRBackupFile -Id <Guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns backup files. You can use this cmdlet to get backup files from an object storage and to move them to the object storage.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies the backup. The cmdlet will return an array of backup files for this backup. | Accepts the CBackup object. To create this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | True | Named | True (ByValue) |
| Id | Specifies an ID of a backup file. The cmdlet will return the backup file with the specified ID. | Guid[] | True | Named | False |
| Path | Specifies a relative path to the folder with backup files. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the [VBRBackupFile](vbrbackupfile.md) object that contains missing backup files.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Backup Files from Specified Backup

|  |  |
| --- | --- |
| This example shows how to get all backup files from the specified backup.  |  | | --- | | $backup = Get-VBRBackup -Name "Exchange backups"  Get-VBRBackupFile -Backup $backup |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the Get-VBRBackupFile cmdlet. Set the $backup variable as the Backup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting all Incremental Backup Files from Specified Backup

|  |  |
| --- | --- |
| This example shows how to get all incremental backup files from the specified backup.  |  | | --- | | $backup = Get-VBRBackup -Name "Exchange backups"  Get-VBRBackupFile -Backup $backup -Path "C:\Users\Administrator\Downloads\.vib" |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the Get-VBRBackupFile cmdlet. Set the $backup variable as the Backup parameter value. Specify the Path parameter value. |

Related Commands

[Get-VBRBackup](get-vbrbackup.md)


