---
title: "Get-VBRViVirtualDevice"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrvivirtualdevice.html"
last_updated: "4/11/2024"
product_version: "13.0.1.1071"
---

# Get-VBRViVirtualDevice


Short Description

Returns details on VMware VM virtual disks.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRViVirtualDevice -RestorePoint <COib>  [<CommonParameters>] |

Detailed Description

This cmdlet returns details on backed-up VMware VM virtual disks. The cmdlet will return details on the following types of virtual disks:

* SCSI
* SATA
* NVME
* IDE

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| RestorePoint | Specifies a restore point of VMs. The cmdlet will return details on backed-up virtual disks of these VMs. | Accepts the COib object. To get this object, run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRViVirtualDevice[] object that contains details on virtual disks of VMs from backups.

Examples

Getting Details on Virtual Disks

This example shows how to get details on virtual disks of the VM that is backed up by the Winsrv4515 backup job.

|  |
| --- |
| $backup = Get-VBRBackup -Name "Winsrv4515"  $restorepoint = Get-VBRRestorePoint -Backup $backup  Get-VBRViVirtualDevice -RestorePoint $restorepoint[3] |

Perform the following steps:

1. Get the restore point:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Set the $backup variable as the Backup parameter value. Save the result to the $restorepoint variable.

The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the fourth restore point is used.

1. Run the Get-VBRViVirtualDevice cmdlet. Set the $restorepoint variable as the RestorePoint parameter value.

The cmdlet output will contain the following details on VM virtual disks: ControllerNumber, Type, VirtualDeviceNode, VirtualDeviceCapacityGB and Name.

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)


