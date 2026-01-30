---
title: "Remove-VBRUnstructuredBackup"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrunstructuredbackup.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRUnstructuredBackup


Short Description

Removes backup files created by the file backup jobs and object storage backup jobs.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Remove backup files created by file backup jobs and object storage backup jobs from the backup infrastructure.

|  |
| --- |
| Remove-VBRUnstructuredBackup -Backup <VBRUnstructuredBackup[]> [-Confirm] [-WhatIf]  [<CommonParameters>] |

* Remove backup files of specific file shares or object storage from the disk.

|  |
| --- |
| Remove-VBRUnstructuredBackup -Backup <VBRUnstructuredBackup[]> -Server <VBRUnstructuredServer[]> [-RunAsync] [-Confirm] [-WhatIf]  [<CommonParameters>] |

* Remove backup files created by the file backup jobs and object storage backup jobs from the disk.

|  |
| --- |
| Remove-VBRUnstructuredBackup -Backup <VBRUnstructuredBackup[]> -FromDisk [-RunAsync] [-Confirm] [-WhatIf]  [<CommonParameters>] |

* Remove the whole backup or a particular restore point from the backup.

|  |
| --- |
| Remove-VBRUnstructuredBackup -RestorePoint <VBRUnstructuredBackupRestorePoint[]> [-RunAsync] [-Confirm] [-WhatIf]  [<CommonParameters>] |

Detailed Description

This cmdlet removes backup files created by the file backup jobs and object storage backup jobs.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Backup | Specifies an array of backup files created by the file backup jobs and object storage backup jobs. The cmdlet will remove these backup files. | Accepts the VBRUnstructuredBackup[] object. To get this object, run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Server | Specifies an array of file shares and object storage. The cmdlet will remove backup files of the specified file shares from the disk. | Accepts the VBRUnstructuredServer[] object. To get this object, run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. | True | Named | False |
| RestorePoint | Specifies an array of restore points. The cmdlet will remove backups that have restore points specified in the array.  Note: If the Backup parameter is also specified, the cmdlet will remove backup files for specified file shares. | Accepts the VBRUnstructuredBackupRestorePoint[] object. To get this object, run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| FromDisk | Defines that the cmdlet will remove backup files from disk. | SwitchParameter | True | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if the user is sure that he wants to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Backup Files from Veeam Backup & Replication Infrastructure

|  |  |
| --- | --- |
| This example shows how to remove the Reports backup backup files from the Veeam Backup & Replication infrastructure.  |  | | --- | | $backupfile = Get-VBRUnstructuredBackup -Name "Reports backup"  Remove-VBRUnstructuredBackup -Backup $backupfile |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backupfile variable. 2. Run the Remove-VBRUnstructuredBackup cmdlet. Set the $backupfile variable as the Backup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Backup Files of Specific Object Storage from Disk

|  |  |
| --- | --- |
| This example shows how to remove the Reports backup of the MinioSrv object storage from a disk.  |  | | --- | | $backupfile = Get-VBRUnstructuredBackup -Name "Reports"  $server = Get-VBRUnstructuredServer -Name "MinioSrv"  Remove-VBRUnstructuredBackup -Backup $backupfile -Server $server |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backupfile variable. 2. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 3. Run the Remove-VBRUnstructuredBackup cmdlet. Set the $backupfile variable as the Backup parameter value. Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Removing Backup Files From Disk

|  |  |
| --- | --- |
| This example shows how to remove the Reports backup file from a disk.  |  | | --- | | $backupfile = Get-VBRUnstructuredBackup -Name "Reports"  Remove-VBRUnstructuredBackup -Backup $backupfile |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backupfile variable. 2. Run the Remove-VBRUnstructuredBackup cmdlet. Set the $backupfile variable as the Backup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Removing Restore Points of File Backups for Specific File Share

|  |  |
| --- | --- |
| This example shows how to remove restore points of the NFS03 backup file created to back up the \\WinSRV2049\Documents file share.  |  | | --- | | $backupfile = Get-VBRUnstructuredBackup -Name "NFS03"  $server = Get-VBRUnstructuredServer -Name "\\WinSRV2049\Documents"  $restorepoint = Get-VBRUnstructuredBackupRestorePoint -Server $server -Backup $backupfile  Remove-VBRUnstructuredBackup -RestorePoint $restorepoint -RunAsync |  Perform the following steps:   1. Run the [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backupfile variable. 2. Run the [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 3. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Set the $server variable as the Server parameter value. Set the $backupfile variable as the Backup parameter value. Save the result to the $restorepoint variable. 4. Run the Remove-VBRUnstructuredBackup cmdlet. Set the $restorepoint as the RestorePoint parameter value. Provide the RunAsync parameter. |

Related Commands

* [Get-VBRUnstructuredBackup](get-vbrunstructuredbackup.md)
* [Get-VBRUnstructuredServer](get-vbrunstructuredserver.md)
* [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md)


