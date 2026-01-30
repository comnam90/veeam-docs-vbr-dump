---
title: "Set-VBRLinuxSelectedVolume"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrlinuxselectedvolume.html"
last_updated: "5/6/2024"
product_version: "13.0.1.1071"
---

# Set-VBRLinuxSelectedVolume


Short Description

Modifies the scope of volumes for Veeam Agent backup jobs that back up Linux machines.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRLinuxSelectedVolume -SelectedVolume <VBRLinuxSelectedVolume> [-Type <VBRLinuxSelectedVolumeType>] [-Path <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies the VBRLinuxSelectedVolume object that specifies the scope of volumes for Veeam Agent Backup jobs that back up Linux machines.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| SelectedVolume | Specifies the volumes that you want to modify. | Accepts the VBRLinuxSelectedVolume object. To get this object, run the [New-VBRLinuxSelectedVolume](new-vbrlinuxselectedvolume.md) cmdlet. | True | Named | False |
| Type | Specifies the type of the volume that you want to back up. You can select the following type of volumes:   * Device - use this option to include in the backup scope all volumes on a computer disk or individual volumes of a protected computer. * MountPoint - use this option to include a mount point in the backup scope. * LVM - use this option to include individual LVM volumes in the backups scope. * BTRFS - use this option to include BTRFS subvolumes in the backup scope. | VBRLinuxSelectedVolumeType | False | Named | False |
| Path | Specifies the path to the volume that you want to include in the backup scope. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRLinuxSelectedVolume object that contains the scope of volumes for Agent Backup jobs that back up Linux machines.

Examples

Modifying Backup Scope for Linux Machines

This example shows how to modify the backup scope for Linux machines. Veeam Agent Backup jobs will back up the second hard disk instead of the first hard disk.

|  |
| --- |
| $volumes = New-VBRLinuxSelectedVolume -Type Device -Path "/dev/sda"  Set-VBRLinuxSelectedVolume -SelectedVolume $volumes -Type Device -Path "/dev/sdb" |

Perform the following steps:

1. Run the [New-VBRLinuxSelectedVolume](new-vbrlinuxselectedvolume.md) cmdlet. Set the Device option for the Type parameter. Specify the Path parameter value. Save the result to the $volumes variable.
2. Run the Set-VBRLinuxSelectedVolume cmdlet. Specify the following settings:

* Set the $volumes variable as the SelectedVolume parameter value.
* Set the Device option for the Type parameter.
* Specify the Path parameter value.

Related Commands

[New-VBRLinuxSelectedVolume](new-vbrlinuxselectedvolume.md)


