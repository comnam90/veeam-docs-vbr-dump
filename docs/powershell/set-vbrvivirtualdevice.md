---
title: "Set-VBRViVirtualDevice"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvivirtualdevice.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---

# Set-VBRViVirtualDevice

In this article

Short Description

Modifies settings of VM virtual disks.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRViVirtualDevice -VirtualDevice <VBRViVirtualDevice> [-ControllerNumber <int>] [-Type <VBRViVirtualDeviceType> {SCSI | SATA | NVME | IDE}] [-VirtualDeviceNode <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of VM virtual disks.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| VirtualDevice | Specifies VM virtual disks. The cmdlet will modify settings of these VM disks. | Accepts the VBRViVirtualDevice object. To get this object, run the [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md) cmdlet. | True | 0 | True (ByValue, ByPropertyName) |
| ControllerNumber | Specifies a controller number for VM virtual disks. The cmdlet will set the specified controller number to the VM virtual disks.  Maximum allowed value: 3. | Int32 | False | Named | False |
| Type | Specifies a virtual device node type. You can specify one of the following virtual device node types:   * SCSI * SATA * NVME * IDE | VBRViVirtualDeviceType | False | Named | False |
| VirtualDeviceNode | Specifies a number of a virtual device node. The cmdlet will set the VM virtual disk with the specified number of a virtual device node. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRViVirtualDevice object that contains details on virtual disks of VMs from backups.

Examples

Modifying VM Virtual Disk Settings

This cmdlet modifies the following settings for VM virtual disks and sets it to the SCSI 0:5. The controller number is set to 0. The number of a virtual device node is set to 5.

|  |
| --- |
| $backup = Get-VBRBackup -Name "Winsrv4515"  $restorepoint = Get-VBRRestorePoint  $disk = Get-VBRViVirtualDevice -RestorePoint $restorepoint[3]  Set-VBRViVirtualDevice -VirtualDevice $disk -ControllerNumber 0 -Type SCSI -VirtualDeviceNode 5 |

Perform the following steps:

1. Get the restore point:

1. Run the [Get-VBRBackup](get-vbrbackup.md) cmdlet. Specify the Name parameter value. Save the result to the $backup variable.
2. Run the [Get-VBRRestorePoint](get-vbrrestorepoint.md) cmdlet. Save the result to the $restorepoint variable.

The Get-VBRRestorePoint cmdlet will return an array of restore points. Consider that the array numbering starts with 0. In our example, the fourth restore point is used.

1. Run the [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md) cmdlet. Set the $restorepoint variable as the RestorePoint parameter value.  Save the result to the $disk variable.

The cmdlet output will contain the following details on VM virtual disks: ControllerNumber, Type, VirtualDeviceNode, VirtualDeviceCapacityGB and Name.

1. Run the Set-VBRViVirtualDevice cmdlet. Specify the following settings:

* Set the $disk variable as the VirtualDevice parameter value.
* Specify the ControllerNumber parameter value.
* Set the SCSI option for the Type parameter.
* Specify the VirtualDeviceNode parameter value.

Related Commands

* [Get-VBRBackup](get-vbrbackup.md)
* [Get-VBRRestorePoint](get-vbrrestorepoint.md)
* [Get-VBRViVirtualDevice](get-vbrvivirtualdevice.md)

Page updated 3/1/2024

Page content applies to build 13.0.1.1071
