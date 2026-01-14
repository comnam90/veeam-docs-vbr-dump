---
title: "Add-VNXSnapshot"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vnxsnapshot.html"
last_updated: "3/6/2024"
product_version: "13.0.1.1071"
---

# Add-VNXSnapshot

In this article

Short Description

Creates Dell VNX storage snapshots.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: Dell VNX

Syntax

|  |
| --- |
| Add-VNXSnapshot -Volume <CSanVolume> [-Name <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a snapshot of a selected Dell VNX storage volume.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Volume | Specifies the storage volume for which you want to take snapshot. | Accepts the CSanVolume object. To get this object, run the [Get-VNXVolume](get-vnxvolume.md) cmdlet. | True | Named | False |
| Name | Specifies the name you want to assign to the snapshot. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Creating Dell VNX Storage Snapshot

This example shows how to create a volume snapshot.

|  |
| --- |
| $storage = Get-VNXHost -Name "VNX Storage"  $volume = Get-VNXVolume -Name "VOLUME1" -Host $storage  Add-VNXSnapshot -Volume $volume -Name "Snapshot01" |

Perform the following steps:

1. Run the [Get-VNXHost](get-vnxhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the [Get-VNXVolume](get-vnxvolume.md) cmdlet. Specify the Name parameter value. Set the $storage variable as the Host parameter value. Save the result to the $volume variable.
3. Run the Add-VNXSnapshot cmdlet. Set the $volume variable as the Volume parameter value. Specify the Name parameter value.

Related Commands

* [Get-VNXHost](get-vnxhost.md)
* [Get-VNXVolume](get-vnxvolume.md)

Page updated 3/6/2024

Page content applies to build 13.0.1.1071
