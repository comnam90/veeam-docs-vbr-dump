---
title: "Get-HP3Snapshot"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-hp3snapshot.html"
last_updated: "2/12/2024"
product_version: "13.0.1.1071"
---

# Get-HP3Snapshot

In this article

Short Description

Returns HPE 3PAR StoreServ storage snapshots.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: HPE 3PAR StoreServ

Syntax

This cmdlet provides parameter sets that allow you to:

* Get HPE 3PAR StoreServ storage snapshots by name.

|  |
| --- |
| Get-HP3Snapshot [-Name <string[]>]  [<CommonParameters>] |

* Get HPE 3PAR StoreServ storage snapshots for volumes.

|  |
| --- |
| Get-HP3Snapshot [-Name <string[]>] [-Volume <CSanVolume[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns existing HPE 3PAR StoreServ storage snapshots.

You can get the list of all storage snapshots, or look for a specific snapshot by name or associated volume.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of the snapshot names. The cmdlet will return the snapshots with these names. | String[] | False | Named | False |
| Volume | Specifies the array of volumes. The cmdlet will return the snapshots of these volumes. | Accepts the CSanVolume[] object. To get this object, run the [Get-HP3Volume](get-hp3volume.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All HPE 3PAR StoreServ Storage Snapshots

|  |  |
| --- | --- |
| This command looks for all existing HPE 3PAR StoreServ storage snapshots.  |  | | --- | | Get-HP3Snapshot | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Snapshots of Several HPE 3PAR StoreServ Storage Volumes

|  |  |
| --- | --- |
| This example shows how to get the existing snapshots of several HPE 3PAR StoreServ storage volumes.  |  | | --- | | $storage = Get-HP3Storage -Name "HPE 3PAR StoreServe Storage"  $volume1 = Get-HP3Volume -Host $storage -Name "VOL01"  $volume2 = Get-HP3Volume -Host $storage -Name "VOL02"  Get-HP3Snapshot -Volume $volume1, $volume2 |  Perform the following steps:   1. Run the [Get-HP3Storage](get-hp3storage.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable. 2. Run the [Get-HP3Volume](get-hp3volume.md) cmdlet. Set the $storage variable as the Host parameter value. Specify the Name parameter value. Save each volume to a separate variable: $volume1, $volume2, etc. 3. Run the Get-HP3Snapshot cmdlet. Set the $volume1 and $volume2 variables as the Volume parameter values. |

Related Commands

* [Get-HP3Storage](get-hp3storage.md)
* [Get-HP3Volume](get-hp3volume.md)

Page updated 2/12/2024

Page content applies to build 13.0.1.1071
