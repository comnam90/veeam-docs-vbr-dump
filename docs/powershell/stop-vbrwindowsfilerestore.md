---
title: "Stop-VBRWindowsFileRestore"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrwindowsfilerestore.html"
last_updated: "10/4/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRWindowsFileRestore


Short Description

Stops Windows guest OS file restore session.

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Stop Windows guest OS file restore session.

|  |
| --- |
| Stop-VBRWindowsFileRestore [-FileRestore <FileRestore>]  [<CommonParameters>] |

* Unmount guest OS disks.

|  |
| --- |
| Stop-VBRWindowsFileRestore [-MountPoint <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet stops Windows guest OS file restore session initiated with the [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) cmdlet.

|  |
| --- |
| Note |
| Note that you cannot restore files after the disks are unmounted. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| FileRestore | Specifies the running Windows guest OS file restore session you want to stop. | Accepts the FileRestore object. To create this object, run the [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) cmdlet. | False | 1 | False |
| MountPoint | Specifies the path to the mounted disk. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Stopping Restore Session of Windows Guest OS Files

|  |  |
| --- | --- |
| This example shows how to stop a restore session of Windows guest OS files of the WinSrv25 machine.  |  | | --- | | $backup = Get-VBRBackup -Name "WinSrv25"  $restorepoint = Get-VBRRestorePoint -Backup $backup -Name "Production VM"  $session = Start-VBRWindowsFileRestore -RestorePoint $restorepoint  Stop-VBRWindowsFileRestore -FileRestore $session |  Perform the following steps:   1. Start the restore session:  1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. 2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Specify the Name parameter value. Save the result to the $restorepoint variable. 3. Run the [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Save the result to the $session variable.  1. Run the Stop-VBRWindowsFileRestore cmdlet. Set the $session variable as the FileRestore parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Unmounting Windows Guest OS Disks

|  |  |
| --- | --- |
| This command unmounts Windows Guest OS Disks from the C:\Disks mount point.  |  | | --- | | Stop-VBRWindowsFileRestore -MountPoint "C:\Disks" | |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Start-VBRWindowsFileRestore](start-vbrwindowsfilerestore.md)


