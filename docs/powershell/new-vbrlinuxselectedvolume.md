---
title: "New-VBRLinuxSelectedVolume"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrlinuxselectedvolume.html"
last_updated: "1/8/2024"
product_version: "13.0.1.1071"
---

# New-VBRLinuxSelectedVolume

In this article

Short Description

Defines the scope of volumes for Veeam Agent backup jobs that back up Linux machines.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRLinuxSelectedVolume -Type {Device | MountPoint | LVM | BTRFS} -Path <string>  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRLinuxSelectedVolume object that specifies the scope of volumes for Agent Backup jobs that back up Linux machines.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Type | Specifies the type of the volume that you want to back up. You can select the following type of volumes:   * Device - use this option to include in the backup scope all volumes on a computer disk or individual volumes of a protected computer. * MountPoint - use this option to include individual volumes of a protected computer in the backup scope. * LVM - use this option to include individual LVM logical volumes in the backups scope. * BTRFS - use this option to include BTRFS subvolumes in the backup scope. | VBRLinuxSelectedVolumeType | True | Named | False |
| Path | Specifies the path to the volume that you want to include in the backup scope. | String | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

This cmdlet returns the VBRLinuxSelectedVolume object that contains the scope of volumes for Agent Backup jobs that back up Linux machines.

Examples

Creating Backup Scope with All Volumes on Computer Disk

This command creates the backup scope that includes all volumes on a computer disk.

|  |
| --- |
| New-VBRLinuxSelectedVolume -Type Device -Path "/dev/sda" |

Page updated 1/8/2024

Page content applies to build 13.0.1.1071
