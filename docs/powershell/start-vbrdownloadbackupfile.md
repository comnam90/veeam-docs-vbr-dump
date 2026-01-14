---
title: "Start-VBRDownloadBackupFile"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrdownloadbackupfile.html"
last_updated: "5/30/2024"
product_version: "13.0.1.1071"
---

# Start-VBRDownloadBackupFile

In this article

Short Description

Downloads backup files from the capacity tier to the performance tier.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Download full backup files.

|  |
| --- |
| Start-VBRDownloadBackupFile -BackupFile <VBRBackupFile[]> [-ThisBackup] [-RunAsync]  [<CommonParameters>] |

* Download full backup files and increments that are related to these backup files.

|  |
| --- |
| Start-VBRDownloadBackupFile -BackupFile <VBRBackupFile[]> [-ThisBackupAndIncrements] [-RunAsync]  [<CommonParameters>] |

Detailed Description

This cmdlet starts the rehydration procedure. Veeam Backup & Replication will download the backup files from the capacity tier to the performance tier. You can use the following scenarios for downloading the backup files:

* Download full backup files only.
* Download full backup files with all incremental backup files.
* Download the incremental backup files with all other increments related to it and the full backup file.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| BackupFile | Specifies an array of backup files that you want to download. | Accepts the [VBRBackupFile[]](vbrbackupfile.md) object. To create this object, run the [Get-VBRBackupFile](get-vbrbackupfile.md) cmdlet. | True | Named | True (ByValue) |
| ThisBackup | Defines that the cmdlet will download full backup files only.  Note: This parameter is not applicable for the backups created with Veeam Plug-in for SAP HANA and Veeam Plug-in for Oracle RMAN. If you provide this parameter, the cmdlet will download full backup files. | SwitchParameter | False | Named | False |
| ThisBackupAndIncrements | Defines that the cmdlet will download full backup files and all backup files that are related to it.  Note: This parameter is not applicable for the backups created with Veeam Plug-in for SAP HANA and Veeam Plug-in for Oracle RMAN. If you provide this parameter, the cmdlet will download full backup files. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Downloading Full Backup File from Capacity Tier

|  |  |
| --- | --- |
| This example shows how to download a full backup file from the capacity tier.  |  | | --- | | $backup = Get-VBRBackup -Name "Exchange backups"  $files = Get-VBRBackupFile -Backup $backup  Start-VBRDownloadBackupFile -BackupFile $files -ThisBackup |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRBackupFile](get-vbrbackupfile.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $files variable. 3. Run the Start-VBRDownloadBackupFile cmdlet. Set the $files variable as the BackupFile parameter value. Provide ThisBackup parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Downloading Full Backup File with all Increments

|  |  |
| --- | --- |
| This example shows how to download a full backup file with all increments related to it from the capacity tier.  |  | | --- | | $backup = Get-VBRBackup -Name "Exchange backups"  $files = Get-VBRBackupFile -Backup $backup  Start-VBRDownloadBackupFile -BackupFile $files -ThisBackupAndIncrements |  Perform the following steps:   1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRBackupFile](get-vbrbackupfile.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $files variable. 3. Run the Start-VBRDownloadBackupFile cmdlet. Set the $files variable as the BackupFile parameter value. Provide the ThisBackupAndIncrements parameter. |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRBackupFile](get-vbrbackupfile.md)

Page updated 5/30/2024

Page content applies to build 13.0.1.1071
