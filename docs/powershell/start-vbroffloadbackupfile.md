---
title: "Start-VBROffloadBackupFile"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbroffloadbackupfile.html"
last_updated: "3/11/2024"
product_version: "13.0.1.1071"
---

# Start-VBROffloadBackupFile


Short Description

Moves backup files to the capacity tier.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Move full backup files to the capacity tier.

|  |
| --- |
| Start-VBROffloadBackupFile -BackupFile <VBRBackupFile[]> [-RunAsync] [-ThisBackup]  [<CommonParameters>] |

* Move the specified backup files with all backup files related to it to the capacity tier.

|  |
| --- |
| Start-VBROffloadBackupFile -BackupFile <VBRBackupFile[]> [-ThisBackupAndIncrements] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts to move backup files to the capacity tier. You can use the following scenarios for moving the backup files:

* Move full backup files only.
* Move full backup files with all increments.
* Move increment backup files with all other increments related to it and a full backup file.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| BackupFile | Specifies an array of backup files that you want to move to the capacity tier. | Accepts the [VBRBackupFile[]](vbrbackupfile.md) object. To create this object, run the [Get-VBRBackupFile](get-vbrbackupfile.md) cmdlet. | True | Named | True (ByValue) |
| ThisBackup | Defines that the cmdlet will move only full backup files to the capacity tier.  Note: This parameter is not applicable for the backups created with Veeam Plug-in for SAP HANA and Veeam Plug-in for Oracle RMAN. If you provide this parameter, the cmdlet will download full backup files. | SwitchParameter | False | Named | False |
| ThisBackupAndIncrements | Defines that the cmdlet will move full backup files and all backup files that are related to it to the capacity tier.  Note: This parameter is not applicable for the backups created with Veeam Plug-in for SAP HANA and Veeam Plug-in for Oracle RMAN. If you provide this parameter, the cmdlet will download full backup files. | SwitchParameter | False | Named | False |
| MoveAlreadyCopiedBackupsToSealedExtent | Defines that the cmdlet will move backup files if the capacity extent is sealed and backups files already copied. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Moving Full Backup File to Capacity Tier

|  |  |
| --- | --- |
| This example shows how to move a full backup file to the capacity tier.  |  | | --- | | $backup = Get-VBRBackup -Name "Exchange backups"  $files = Get-VBRBackupFile -Backup $backup  Start-VBROffloadBackupFile -BackupFile $files -ThisBackup |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRBackupFile](get-vbrbackupfile.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $files variable. 3. Run the Start-VBROffloadBackupFile cmdlet. Set the $files variable as the BackupFile parameter value. Provide the ThisBackup parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Moving Full Backup File with Increments to Capacity Tier

|  |  |
| --- | --- |
| This example shows how to move a full backup file with all increments related to it to the capacity tier.  |  | | --- | | $backup = Get-VBRBackup -Name "Exchange backups"  $files = Get-VBRBackupFile -Backup $backup  Start-VBROffloadBackupFile -BackupFile $files -ThisBackupAndIncrements |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRBackupFile](get-vbrbackupfile.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $files variable. 3. Run the Start-VBROffloadBackupFile cmdlet. Set the $files variable as the Backupfile parameter value. Provide the ThisBackupAndIncrements parameter. |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRBackupFile](get-vbrbackupfile.md)


