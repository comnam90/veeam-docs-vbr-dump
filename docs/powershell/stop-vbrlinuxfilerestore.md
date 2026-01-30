---
title: "Stop-VBRLinuxFileRestore"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/stop-vbrlinuxfilerestore.html"
last_updated: "8/16/2024"
product_version: "13.0.1.1071"
---

# Stop-VBRLinuxFileRestore


Short Description

Stops Linux-based or Unix-based guest OS files restore.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Stop-VBRLinuxFileRestore -LinuxFlrObject <VBRLinuxFlrObject>  [<CommonParameters>] |

Detailed Description

This cmdlet stops Linux-based or Unix-based guest OS file restore process started with the [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) cmdlet.

When you stop the OS file restore, Veeam Backup & Replication unmounts virtual disks and powers the proxy appliance off.

|  |
| --- |
| Note |
| You cannot restore files after the disks are unmounted. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| LinuxFlrObject | Specifies the Linux file restore process initiated by  that you want to stop. | Accepts the VBRLinuxFlrObject object. To create this object, run the [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) cmdlet. | True | Named | True (ByValue, |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Stopping Linux-Based Guest OS File Restore

This example shows how to stop a restore session of Linux or Unix-based guest OS files of the UbuntuSrv machine.

|  |
| --- |
| $backup = Get-VBRBackup -Name "UbuntuSrv"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $server = Get-VBRServer -Name "ESXi01"  $resourcepool = Find-VBRViResourcePool -Server $server -Name "Servers"  $session = Start-VBRLinuxFileRestore -RestorePoint $restorepoint -Server $server -ResourcePool $resourcepool  Stop-VBRLinuxFileRestore -LinuxFlrObject $session |

Perform the following steps:

1. Start a restore session:

* Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
* Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable the Backup parameter value. Save the result to the $restorepoint variable.
* Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
* Run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. Set the $server variable the Server parameter value. Specify the Name parameter values. Save the result to the $resourcepool variable.
* Run the [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) cmdlet. Set the RestorePoint variable the RestorePoint parameter value. Set the $server variable the Server parameter value. Set the $resourcepool variable the ResourcePool parameter value. Save the result to the $session variable.

1. Run the Stop-VBRLinuxFileRestore cmdlet. Set the $session variable as the LinuxFlrObject parameter value.

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRServer](get-vbrserver.md)
* [Find-VBRViResourcePool](find-vbrviresourcepool.md)
* [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md)


