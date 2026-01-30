---
title: "Remove-VBREncryptedBackup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrencryptedbackup.html"
last_updated: "4/1/2025"
product_version: "13.0.1.1071"
---

# Remove-VBREncryptedBackup


Short Description

Removes selected encrypted backups.

|  |
| --- |
| Note |
| If the four-eyes authorization is enabled, you cannot run this cmdlet. For more information, see the [Four-Eyes Authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) section in the User Guide for VMware vSphere. |

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Remove selected encrypted backups from the database.

|  |
| --- |
| Remove-VBREncryptedBackup -Backup <VBRImportedEncryptedBackup[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Remove selected encrypted backups from the disk.

|  |
| --- |
| Remove-VBREncryptedBackup -Backup <VBRImportedEncryptedBackup[]> -FromDisk [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes selected encrypted backups. When you remove backups, you can use the following options:

* Remove from database. When you remove a backup from the database, you remove records about the backup from the Veeam configuration database. The backup files remain in the repository. Any type of backup can be removed with this option.

* Remove from disk. With this option, the backup is removed from the database and from the disk. This removal is complete and non-reversible. Cloud Connect backups cannot be removed with this option.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies the array of backups you want to remove. | Accepts the VBRImportedEncryptedBackup[] object. To get this object, run the [Get-VBREncryptedBackup](get-vbrbackup.md) cmdlet. | True | 0 | True (ByValue, ByProperty Name) |
| FromDisk | Defines that the cmdlet will delete backups from disk. If you do not provide this parameter, the cmdlet will delete only the information about the backups.  Note: You must provide this parameter to remove backups from archive extents and capacity extents. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwichParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Specific Encrypted Backups from Database [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to remove the encrypted backups named Backup Job 01 and Backup Job 02 from the database.  |  | | --- | | Get-VBREncryptedBackup -Name "Backup Job 01", "Backup Job 02" | Remove-VBREncryptedBackup |  Perform the following steps:   1. Run the [Get-VBREncryptedBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Remove-VBREncryptedBackup cmdlet. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Encrypted Backups from Disk with Specified Names [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to remove encrypted backups ending with 2012 characters from the disk.  |  | | --- | | Get-VBREncryptedBackup -Name \*2012 | Remove-VBREncryptedBackup -FromDisk |  Perform the following steps:   1. Run the [Get-VBREncryptedBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. 2. Pipe the cmdlet output to the Remove-VBREncryptedBackup cmdlet. Provide the FromDisk parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Removing Encrypted Backup from Disk [Using Variable]

|  |  |
| --- | --- |
| This example shows how to delete encrypted backups from the disk.  |  | | --- | | $backup = Get-VBREncryptedBackup -Name "Backups"  Remove-VBREncryptedBackup -Backup $backup -FromDisk |  Perform the following steps:   1. Run the [Get-VBREncryptedBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the Remove-VBREncryptedBackup cmdlet. Set the $backup variable as the Backup parameter value. Provide the FromDisk parameter. |

Related Commands

* [Get-VBREncryptedBackup](get-vbrbackup.md)


