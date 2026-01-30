---
title: "Remove-VBRBackupFile"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrbackupfile.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRBackupFile


Short Description

Removes missing backup files from the Veeam Backup & Replication configuration database.

|  |
| --- |
| Note |
| If the four-eyes authorization is enabled, you cannot run this cmdlet. For more information, see the [Four-Eyes Authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) section in the User Guide for VMware vSphere. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Remove a missing backup file and all backup files related to it.

|  |
| --- |
| Remove-VBRBackupFile -BackupFile <VBRBackupFile> [-FromDisk] [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Remove all backup files that are missing from a backup.

|  |
| --- |
| Remove-VBRBackupFile -Backup <CBackup> [-FromDisk] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes missing backup files from the Veeam Backup & Replication configuration database.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| BackupFile | Specifies a missing backup file that you want to remove. | Accepts the [VBRBackupFile](vbrbackupfile.md) object. To create this object, run the [Get-VBRBackupFile](get-vbrbackupfile.md) cmdlet. | True | Named | False |
| Backup | Specifies a backup from which you want to remove missing backup files. | Accepts the CBackup object. To create this object, run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. | True | Named | False |
| FromDisk | Defines that the cmdlet will remove the missing backup files from the configuration database and from disk (if these backup files are still available). If you do not provide this parameter, the cmdlet will remove missing backup files from the configuration database only. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Missing Backup File

|  |  |
| --- | --- |
| This example shows how to remove a missing backup file and all backup files related to it from Veeam Backup & Replication configuration database.  |  | | --- | | $backup = Get-VBRBackup -Name "Daily backups"  $missingfile = Get-VBRBackupFile -Backup $backup[4]  Remove-VBRBackupFile -BackupFile $missingfile -Confirm |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRBackupFile](get-vbrbackupfile.md) cmdlet. Set the $backup[4] variable as the Backup parameter value. Save the result to the $missingfile variable. 3. Run the Remove-VBRBackupFile cmdlet. Set the $missingfile variable as the BackupFile parameter value. Provide the Confirm parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing all Missing Backup Files from Backup

|  |  |
| --- | --- |
| This example shows how to remove all backup files that are missing from a backup. The cmdlet will remove the files from the configuration database and from disk.  |  | | --- | | $backup = Get-VBRBackup -Name "Daily backups"  Remove-VBRBackupFile -Backup $backup -FromDisk |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the Remove-VBRBackupFile cmdlet. Set the $backup variable as the Backup parameter value. Provide the FromDisk parameter. |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRBackupFile](get-vbrbackupfile.md)


