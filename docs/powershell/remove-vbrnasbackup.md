---
title: "Remove-VBRNASBackup (obsolete)"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrnasbackup.html"
last_updated: "1/6/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRNASBackup (obsolete)


Short Description

Removes backup files created by the file backup job.

|  |
| --- |
| Note |
| This cmdlet is obsolete. Run the [Remove-VBRUnstructuredBackup](remove-vbrunstructuredbackup.md) cmdlet instead. |

|  |
| --- |
| Note |
| If the four-eyes authorization is enabled, you cannot run this cmdlet. For more information, see the [Four-Eyes Authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) section in the User Guide for VMware vSphere. |

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Remove backup files created by the file backup job from the Veeam Backup & Replication infrastructure.

|  |
| --- |
| Remove-VBRNASBackup -NASBackup <VBRNASBackup[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Remove backup files of specific file shares from the disk.

|  |
| --- |
| Remove-VBRNASBackup -NASBackup <VBRNASBackup[]> -NASServer <VBRNASServer[]> [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Remove backup files created by the file backup job from the disk.

|  |
| --- |
| Remove-VBRNASBackup -NASBackup <VBRNASBackup[]> -FromDisk [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

* Remove the whole backup or a particular file share from the backup.

|  |
| --- |
| Remove-VBRNASBackup -RestorePoint <VBRNASBackupRestorePoint[]> [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes backup files created by the file backup job.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| NASBackup | Specifies an array of backup files created by the file backup job. The cmdlet will remove these backup files. | Accepts the VBRNASBackup[] object. To create this object, run the [Get-VBRNASBackup](get-vbrnasbackup.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| NASServer | Specifies an array of file shares. The cmdlet will remove backup files of the specified file shares. | Accepts the VBRNASServer[] object. To create this object, run the [Get-VBRNASServer](get-vbrnasserver.md) cmdlet. | True | Named | False |
| RestorePoint | Specifies an array of restore points. The cmdlet will remove backups that have restore points specified in the array.  If the NASBackup parameter is also specified, the cmdlet will remove backup files for specified file shares. | Accepts the VBRNASBackupRestorePoint[] object. To create this object, run the [Get-VBRNASBackupRestorePoint](get-vbrnasbackuprestorepoint.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| FromDisk | Defines that the cmdlet will remove backup files from disk. | SwitchParamter | True | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParamter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParamter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if the user is sure that he wants to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Backup Files from Veeam Backup & Replication Infrastructure

|  |  |
| --- | --- |
| This example shows how to remove the Reports backup backup files from the Veeam Backup & Replication infrastructure.  |  | | --- | | $backupfile = Get-VBRNASBackup -Name "Reports backup"  Remove-VBRNASBackup -NASBackup $backupfile |  Perform the following steps:   1. Run the [Get-VBRNASBackup](get-vbrnasbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backupfile variable. 2. Run the Remove-VBRNASBackup cmdlet. Set the $backupfile variable as the NASBackup parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Backup Files of Specific File Shares from Disk

|  |  |
| --- | --- |
| This example shows how to remove the Reports backup of the \\WinSRV2049\Documents file share from a disk.  |  | | --- | | $backupfile = Get-VBRNASBackup -Name "Reports"  $server = Get-VBRNASServer -Name "\\WinSRV2049\Documents"  Remove-VBRNASBackup -NASBackup $backupfile -NASServer $server |  Perform the following steps:   1. Run the [Get-VBRNASBackup](get-vbrnasbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backupfile variable. 2. Run the [Get-VBRNASServer](get-vbrnasserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 3. Run the Remove-VBRNASBackup cmdlet. Set the $backupfile variable as the NASBackup parameter value. Set the $server variable as the NASServer parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Removing Backup Files From Disk

|  |  |
| --- | --- |
| This example shows how to remove the Reports backup file from a disk.  |  | | --- | | $backupfile = Get-VBRNASBackup -Name "Reports"  Remove-VBRNASBackup -NASBackup $backupfile -FromDisk |  Perform the following steps:   1. Run the [Get-VBRNASBackup](get-vbrnasbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backupfile variable. 2. Run the Remove-VBRNASBackup cmdlet. Set the $backupfile variable as the NASBackup parameter value. Provide the FromDisk parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Removing Restore Points of File Backups for Specific File Share

|  |  |
| --- | --- |
| This example shows how to remove restore points of the NFS03 backup file created to back up the \\WinSRV2049\Documents file share.  |  | | --- | | $backupfile = Get-VBRNASBackup -Name "NFS03"  $server = Get-VBRNASServer -Name "\\WinSRV2049\Documents"  $restorepoint = Get-VBRUnstructuredBackupRestorePoint -NASServer $server -NASBackup $backupfile  Remove-VBRNASBackup -RestorePoint $restorepoint -RunAsync |  Perform the following steps:   1. Run the [Get-VBRNASBackup](get-vbrnasbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backupfile variable. 2. Run the [Get-VBRNASServer](get-vbrnasserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 3. Run the [Get-VBRUnstructuredBackupRestorePoint](get-vbrunstructuredbackuprestorepoint.md) cmdlet. Set the $server variable as the NASServer parameter value. Set the $backupfile variable as the NASBackup parameter value. 4. Run the Remove-VBRNASBackup cmdlet. Set the $restorepoint as the RestorePoint parameter value. Provide the RunAsync parameter. |

Related Commands

* [Get-VBRNASBackup](get-vbrnasbackup.md)
* [Get-VBRNASServer](get-vbrnasserver.md)
* [Get-VBRNASBackupRestorePoint](get-vbrnasbackuprestorepoint.md)


