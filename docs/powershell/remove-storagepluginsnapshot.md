---
title: "Remove-StoragePluginSnapshot"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-storagepluginsnapshot.html"
last_updated: "3/4/2024"
product_version: "13.0.1.1071"
---

# Remove-StoragePluginSnapshot

In this article

Short Description

Removes snapshots of Universal Storage API integrated systems.

|  |
| --- |
| Note |
| If the four-eyes authorization is enabled, you cannot run this cmdlet. For more information, see the [Four-Eyes Authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) section in the User Guide for VMware vSphere. |

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: IBM Spectrum Virtualize, INFINIDAT InfiniBox, Pure Storage

Syntax

|  |
| --- |
| Remove-StoragePluginSnapshot -Snapshot <CSanSnapshot[]>  [<CommonParameters>] |

Detailed Description

This cmdlet permanently removes a selected storage snapshot from your virtual infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Snapshot | Specifies the array of snapshots. The cmdlet will remove these snapshots. | Accepts the CSanSnapshot[] object. To get this object, run the [Get-StoragePluginSnapshot](get-storagepluginsnapshot.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Removing Snapshots of Several Volumes

This example shows how to remove snapshots of several volumes.

|  |
| --- |
| $storage = Get-StoragePluginHost -Name "IBM Spectrum"  $volume1 = Get-StoragePluginVolume -Host $storage -Name "VOLUME-01"  $volume2 = Get-StoragePluginVolume -Host $storage -Name "VOLUME-02"  $snapshot = Get-StoragePluginSnapshot -Volume $volume1, $volume2  Remove-StoragePluginSnapshot -Snapshot $snapshot |

Perform the following steps:

1. Get the volume snapshots you want to remove. To do this, perform the following steps:

* Run the [Get-StoragePluginHost](get-storagepluginhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
* Run the [Get-StoragePluginVolume](get-storagepluginvolume.md) cmdlet. Set the $storage variable as the Host parameter value. Specify the Name parameter value. Save each volume to a separate variable: $volume1, $volume2, etc.
* Run the [Get-StoragePluginSnapshot](get-storagepluginsnapshot.md) cmdlet. Set the $volume1 and $volume2 variables as the Volume parameter value. Save the result to the $snapshot variable.

1. Run the Remove-StoragePluginSnapshot cmdlet. Set the $snapshot variable as the Snapshot parameter value.

Related Commands

* [Get-StoragePluginHost](get-storagepluginhost.md)
* [Get-StoragePluginVolume](get-storagepluginvolume.md)
* [Get-StoragePluginSnapshot](get-storagepluginsnapshot.md)

Page updated 3/4/2024

Page content applies to build 13.0.1.1071
