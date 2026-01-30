---
title: "Get-StoragePluginSnapshot"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-storagepluginsnapshot.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Get-StoragePluginSnapshot


Short Description

Returns snapshots of Universal Storage API integrated systems.

Applies to

Platform: VMware

Product Edition: Enterprise Plus, Veeam Universal License

Storage System: IBM Spectrum Virtualize, INFINIDAT InfiniBox, Pure Storage

Syntax

|  |
| --- |
| Get-StoragePluginSnapshot [-Name <String[]>] [-Volume <CSanVolume[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns snapshots of Universal Storage API integrated systems.

You can get the list of all storage snapshots, or look for a specific snapshot by name or associated volume.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of snapshot names. The cmdlet will return the snapshots with these names. | String[] | False | Named | False |
| Volume | Specifies the array of storage volumes. The cmdlet will return the snapshots of these volumes. | Accepts the CSanVolume[] object. To get the object, run the [Get-StoragePluginVolume](get-storagepluginvolume.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Storage Snapshot by Name

|  |  |
| --- | --- |
| This example shows how to get a storage snapshot by name. The cmdlet will look for the snapshot across all Universal Storage API integrated systems.  |  | | --- | | Get-StoragePluginSnapshot -Name "DailySnapshot01" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2.Getting Snapshots of Several Storage Volumes

|  |  |
| --- | --- |
| This example shows how to get snapshots of several storage volumes.  |  | | --- | | $storage = Get-StoragePluginHost -Name "IBM Spectrum"  $volume1 = Get-StoragePluginVolume -Host $storage -Name "VOLUME-01"  $volume2 = Get-StoragePluginVolume -Host $storage -Name "VOLUME-02"  Get-StoragePluginSnapshot -Volume $volume1, $volume2 |  Perform the following steps:   1. Run the [Get-StoragePluginHost](get-storagepluginhost.md) cmdlet. Save the result to the $storage variable. 2. Get the volumes. To do this, run the [Get-StoragePluginVolume](get-storagepluginvolume.md) cmdlet. Set the $storage variable as the Host parameter value. Specify the Name parameter value. Save each volume to a separate variable: $volume1, $volume2, etc. 3. Run the Get-StoragePluginSnapshot cmdlet. Set the $volume1 and $volume2 variables as the Volume parameter value. |

Related Commands

* [Get-StoragePluginHost](get-storagepluginhost.md)
* [Get-StoragePluginVolume](get-storagepluginvolume.md)


