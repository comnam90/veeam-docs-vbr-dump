---
title: "Get-VBRLinuxGuestItem"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrlinuxguestitem.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Get-VBRLinuxGuestItem

In this article

Short Description

Returns Linux-based or Unix-based guest OS files.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all Linux-based or Unix-based guest OS files.

|  |
| --- |
| Get-VBRLinuxGuestItem -LinuxFlrObject <VBRLinuxFlrObject>  [<CommonParameters>] |

* Get Linux-based or Unix-based guest OS files by specifying the path where these file are located.

|  |
| --- |
| Get-VBRLinuxGuestItem -LinuxFlrObject <VBRLinuxFlrObject> [-Path <string[]>]  [<CommonParameters>] |

* Get child guest OS files of Linux-based or Unix-based guest OS.

|  |
| --- |
| Get-VBRLinuxGuestItem -LinuxFlrObject <VBRLinuxFlrObject> [-ParentItem <VBRFLRItem>] [-Name <string[]>] [-RecursiveSearch]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Linux-based or Unix-based OS files.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| LinuxFlrObject | For getting root guest OS files.  Specifies a running restore session of Linux-based or Unix-based guest OS files. The cmdlet will return files and folders that are available for restore on disks when you run this session. | Accepts the VBRLinuxFlrObject object. To create this object, run the [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Path | Specifies a path to the folder where guest OS files that you want to restore are located. | String[] | False | Named | True (ByPropertyName |
| ParentItem | For getting child guest OS files.  Returns child folders and files that are available from backups of Linux-based or Unix-based machines. | Accepts the VBRFLRItem object. To create this object, run the Get-VBRLinuxGuestItem cmdlet. | False | Named | True (ByPropertyName) |
| Name | Specifies an array of names for items that are available on disks. The cmdlet will return items with these names. | String[] | False | Named | False |
| RecursiveSearch | Defines that the cmdlet will look for items that are added to the specified folders and to all child folders.  If you provide this parameter, the cmdlet will return an array of all items that are added to Linux-based or Unix-based machines. Otherwise, the cmdlet will return an array of items that are added to the parent folder on Linux-based or Unix-based machines. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRFLRItem object that returns files and folders that are available for restore on disks of Linux-based or Unix-based machines.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Root Items Added to Linux-Based Machine

|  |  |
| --- | --- |
| This example shows how to get all root items from disks that are added to the UbuntuSrv Linux-based machine.  |  | | --- | | $backup = Get-VBRBackup -Name "UbuntuSrv"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $server = Get-VBRServer -Name "LinSrv05"  $session = Start-VBRLinuxFileRestore -RestorePoint $restorepoint -MountServer $server  Get-VBRLinuxGuestItem -LinuxFlrObject $session |  Perform the following steps:   1. Start the restore session:  * Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. * Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable. * Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. * Run the [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Set the $server variable as the MountServer parameter value. Save the result to the $session variable.  1. Run the Get-VBRLinuxGuestItem cmdlet. Set the $session variable as the LinuxFlrObject parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Linux-Based Guest OS Files Using Path to Folder

|  |  |
| --- | --- |
| This example shows how to get Linux-based guest OS files added to the UbuntuSrv Linux-based machine. The cmdlet will get all child items added to the /home/administrator/mydir folder.  |  | | --- | | $backup = Get-VBRBackup -Name "UbuntuSrv"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $server = Get-VBRServer -Name "LinSrv05"  $session = Start-VBRLinuxFileRestore -RestorePoint $restorepoint -MountServer $server  Get-VBRLinuxGuestItem -LinuxFlrObject $session -Path "/home/administrator/mydir" |  Perform the following steps:   1. Start the restore session:  * Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. * Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable. * Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. * Run the [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Set the $server variable as the MountServer parameter value. Save the result to the $session variable.  1. Run the Get-VBRLinuxGuestItem cmdlet. Set the $session variable as the LinuxFlrObject parameter value. Specify the Path parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Getting Child Items Added to Unix-Based Machine

|  |  |
| --- | --- |
| This example shows how to get all child items from disks that are added to the Srv2067 Unix-based machine.  |  | | --- | | $backup = Get-VBRBackup -Name "Srv2067"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $server = Get-VBRServer -Name "Mount2067"  $session = Start-VBRLinuxFileRestore -RestorePoint $restorepoint -MountServer $server  $root = Get-VBRLinuxGuestItem -LinuxFlrObject $session  Get-VBRLinuxGuestItem -LinuxFlrObject $session -ParentItem $root |  Perform the following steps:   1. Start the restore session:  * Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable. * Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable. * Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. * Run the [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value. Set the $server variable as the MountServer parameter value. Save the result to the $session variable.  1. Run the Get-VBRLinuxGuestItem cmdlet. Set the $session variable as the LinuxFlrObject parameter value. Save the result to the $root variable.  1. Run the Get-VBRLinuxGuestItem cmdlet. Set the $session variable as the LinuxFlrObject parameter value. Set the $root variable as the ParentItem parameter value. |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRServer](get-vbrserver.md)
* [Start-VBRLinuxFileRestore](start-vbrlinuxfilerestore.md)

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
