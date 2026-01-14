---
title: "Remove-VNXSnapshot"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vnxsnapshot.html"
last_updated: "4/19/2024"
product_version: "13.0.1.1071"
---

# Remove-VNXSnapshot

In this article

Short Description

Removes Dell VNX storage snapshots.

|  |
| --- |
| Note |
| If the four-eyes authorization is enabled, you cannot run this cmdlet. For more information, see the [Four-Eyes Authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) section in the User Guide for VMware vSphere. |

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: Dell VNX

Syntax

|  |
| --- |
| Remove-VNXSnapshot -Snapshot <CSanSnapshot[]>  [<CommonParameters>] |

Detailed Description

This cmdlet permanently removes a selected Dell VNX storage snapshot from your virtual infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Snapshot | Specifies the array of snapshots. The cmdlet will remove these snapshots. | Accepts the CSanSnapshot[] object. To get this object, run the [Get-VNXSnapshot](get-vnxsnapshot.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Removing Snapshots of Several Dell VNX Storage Volumes

This example shows how to remove snapshots of several Dell VNX storage volumes.

|  |
| --- |
| $storage = Get-VNXHost -Name "VNX Storage"  $volume1 = Get-VNXVolume -Host $storage -Name "VOLUME1"  $volume2 = Get-VNXVolume -Host $storage -Name "VOLUME2"  $snapshot = Get-VNXSnapshot -Volume $volume1, $volume2  Remove-VNXSnapshot -Snapshot $snapshot |

Perform the following steps:

1. Get the volume snapshots you want to remove.

* Run the [Get-VNXHost](get-vnxhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
* Run the [Get-VNXVolume](get-vnxvolume.md) cmdlet. Set the $storage variable as the Host parameter value. Specify the Name parameter value. Save each volume to a separate variable: $volume1, $volume2, etc.
* Run the [Get-VNXSnapshot](get-vnxsnapshot.md) cmdlet. Set the $volume1 and $volume2 variables as the Volume parameter values. Save the result to the $snapshot variable.

1. Run the Remove-VNXSnapshot cmdlet. Set the $snapshot variable as the Snapshot parameter value.

Related Commands

* [Get-VNXHost](get-vnxhost.md)
* [Get-VNXVolume](get-vnxvolume.md)
* [Get-VNXSnapshot](get-vnxsnapshot.md)

Page updated 4/19/2024

Page content applies to build 13.0.1.1071
