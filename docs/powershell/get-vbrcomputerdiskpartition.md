---
title: "Get-VBRComputerDiskPartition"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcomputerdiskpartition.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-VBRComputerDiskPartition


Short Description

Returns volumes of computers backed-up with Veeam Agent for Microsoft Windows.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get all volumes of computers backed-up with Veeam Agent for Microsoft Windows.

|  |
| --- |
| Get-VBRComputerDiskPartition -RestorePoint <COib>  [<CommonParameters>] |

* Get specific volumes of computers backed-up with Veeam Agent for Microsoft Windows.

|  |
| --- |
| Get-VBRComputerDiskPartition -RestorePoint <COib> -Disk <VBRComputerDisk[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns volumes of computers backed-up with Veeam Agent for Microsoft Windows.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point of computers. The cmdlet will return details on backed-up volumes of these computers. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Disk | Specifies computer disks. The cmdlet will return details on these disks. | Accepts the VBRComputerDisk[] object. To create this object, run the [Get-VBRComputerDisk](get-vbrcomputerdisk.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRComputerDiskPartition object that contains volumes of computers backed-up with Veeam Agent for Microsoft Windows.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting all Volumes of Computers Backed-Up with Veeam Agent for Microsoft Windows

|  |  |
| --- | --- |
| This example shows how get all volumes of the WinLaptop2017 computer backed-up with Veeam Agent for Microsoft Windows.  |  | | --- | | $backup = Get-VBRBackup -Name "WinLaptop2017\*"  $restorepoint = Get-VBRRestorePoint -Backup $backup  Get-VBRComputerDiskPartition -RestorePoint $restorepoint[3] |  Perform the following steps:   1. Get the restore point:  1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.   Note: To get a list of restore points for a Veeam Agent job, you must provide the asterisks sign for the Name parameter value: Name "AgentJob\*". Otherwise, the Get-VBRRestorePoint cmdlet will not return any restore points for the Veeam Agent job.   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the fourth restore point in the array).   1. Run the Get-VBRComputerDiskPartition cmdlet. Set the $restorepoint[3] variable as the RestorePoint parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Specific Volumes of Computers Backed-Up with Veeam Agent for Microsoft Windows

|  |  |
| --- | --- |
| This example shows how to get specific volumes of the WinLaptop2017 computer backed-up with Veeam Agent for Microsoft Windows.  |  | | --- | | $backup = Get-VBRBackup -Name "WinLaptop2017\*"  $restorepoint = Get-VBRRestorePoint -Backup $backup  $disk = Get-VBRComputerDisk -RestorePoint $restorepoint[3]  Get-VBRComputerDiskPartition -RestorePoint $restorepoint[3] -Disk $disk[2] |  Perform the following steps:   1. Get the restore point:  1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.   Note: To get a list of restore points for a Veeam Agent job, you must provide the asterisks sign for the Name parameter value: Name "AgentJob\*". Otherwise, the Get-VBRRestorePoint will not return any restore points for the Veeam Agent job.   1. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable.   The Get-VBRRestorePoint cmdlet will return an array of restore points. Mind the ordinal number of the necessary restore point (in our example, it is the fourth restore point in the array).   1. Run the [Get-VBRComputerDisk](get-vbrcomputerdisk.md) cmdlet. Set the $restorepoint[3] variable as the RestorePoint parameter value. Save the result to the $disk variable.   The Get-VBRComputerDisk cmdlet will return an array of volumes. Mind the ordinal number of the necessary volumes (in our example, it is the third volume in the array).   1. Run the Get-VBRComputerDiskPartition cmdlet. Set the $restorepoint[3] variable as the RestorePoint parameter value. Set the $disk[2] variable as the Disk parameter value. |

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRComputerDisk](get-vbrcomputerdisk.md)


