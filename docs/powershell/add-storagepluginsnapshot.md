---
title: "Add-StoragePluginSnapshot"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-storagepluginsnapshot.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Add-StoragePluginSnapshot

In this article

Short Description

Creates snapshots of Universal Storage API integrated systems.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: IBM Spectrum Virtualize, INFINIDAT InfiniBox, Pure Storage

Syntax

|  |
| --- |
| Add-StoragePluginSnapshot -Volume <CSanVolume> [-Name <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a snapshot of a selected storage volume.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Volume | Specifies the storage volume for which you want to take snapshot. | Accepts the CSanVolume object. To get this object, run the [Get-StoragePluginVolume](get-storagepluginvolume.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the name you want to assign to the snapshot. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Creating Volume Snapshot

This example shows how to create a volume snapshot.

|  |
| --- |
| $storage = Get-StoragePluginHost -Name "IBM Spectrum"  $volume = Get-StoragePluginVolume -Host $storage -Name "VOLUME-01"  Add-StoragePluginSnapshot -Volume $volume -Name "DailySnapshot01" |

Perform the following steps:

1. Run the [Get-StoragePluginHost](get-storagepluginhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the [Get-StoragePluginVolume](get-storagepluginvolume.md) cmdlet. Set the $storage variable as the Host parameter value. Specify the Name parameter value. Save the result to the $volume variable.
3. Run the Add-StoragePluginSnapshot cmdlet. Set the $volume variable as the Volume parameter value. Specify the Name parameter value.

Related Commands

* [Get-StoragePluginHost](get-storagepluginhost.md)
* [Get-StoragePluginVolume](get-storagepluginvolume.md)

Page updated 2/16/2024

Page content applies to build 13.0.1.1071
