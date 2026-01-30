---
title: "Start-VBRRestoreVMFiles"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/start-vbrrestorevmfiles.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Start-VBRRestoreVMFiles


Short Description

Restores VM configuration files.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Start-VBRRestoreVMFiles -RestorePoint <COib> -Server <CHost> -Path <string> [-Files <COIBFileInfo[]>] [-Reason <string>] [-RunAsync] [-Force]  [<CommonParameters>] |

Detailed Description

This cmdlet allows you to restore configuration file (.vmx) or virtual disks (.vmdk) of a selected VM.

|  |
| --- |
| ![Start-VBRRestoreVMFiles](images/icon_note.webp) Note: |
| Run the [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) cmdlet to restore Windows VM guest OS files. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies the VM restore point to which you want to restore. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 1 | True (ByValue, ByProperty Name) |
| Server | Specifies the host to which the VM guest files should be restored. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | 2 | False |
| Path | Specifies the string with the path to the folder where restored files should be saved. | String | True | 3 | False |
| Files | Specifies the files you want to restore.  By default, all files from the VM will be restored. | Accepts the COIBFileInfo[] object. To get this object, run the [Get-VBRFilesInRestorePoint](get-vbrfilesinrestorepoint.md) cmdlet. | False | Named | True (ByProperty Name) |
| Reason | Specifies the string with the reason for performing the VM guest OS file restore. | String | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | False |
| Force | Defines that the cmdlet will restore VM configuration files even if the location of the repository where VM backups reside and the target host location do not match. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Restoring All VM Guest OS Files

This example shows how to restore all VM guest OS files and save them on the Server007 host to the C:\BackupFiles folder.

|  |
| --- |
| $point = Get-VBRBackup -Name "MSExchange Backup" | Get-VBRRestorePoint -Name "MSExchange02" | Sort-Object CreationTime -Descending | Select -First 1  $server = Get-VBRServer -Name "Server007"  Start-VBRRestoreVMFiles –RestorePoint $point –Server $server –Path “C:\BackupFiles” |

Perform the following steps:

1. Get the restore point of the VM that you want to restore:

* Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value.
* Pipe the cmdlet output to the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Specify the Name parameter value.
* Pipe the cmdlet output to the Sort-Object cmdlet and specify the CreationTime parameter value.
* Pipe the cmdlet output to the Select cmdlet. Specify the First parameter value.
* Save the result to the $restorepoint variable.

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value.
2. Run the Start-VBRRestoreVMFiles cmdlet. Set the $point variable as the RestorePoint parameter value. Set the $server variable as the Server parameter value. Specify the Path parameter value.

Related Commands

* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRFilesInRestorePoint](get-vbrfilesinrestorepoint.md)


