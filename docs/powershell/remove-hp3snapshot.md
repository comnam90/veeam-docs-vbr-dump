---
title: "Remove-HP3Snapshot"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-hp3snapshot.html"
last_updated: "3/4/2024"
product_version: "13.0.1.1071"
---

# Remove-HP3Snapshot

In this article

Short Description

Removes HPE 3PAR StoreServ storage snapshots.

|  |
| --- |
| Note |
| If the four-eyes authorization is enabled, you cannot run this cmdlet. For more information, see the [Four-Eyes Authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) section in the User Guide for VMware vSphere. |

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: HPE 3PAR StoreServ

Syntax

|  |
| --- |
| Remove-HP3Snapshot -Snapshot <CSanSnapshot[]>  [<CommonParameters>] |

Detailed Description

This cmdlet permanently removes a selected HPE 3PAR StoreServ storage snapshot from your virtual infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Snapshot | Specifies the array of  snapshots. The cmdlet will remove these snapshots. | Accepts the CSanSnapshot[] object. To get this object, run the [Get-HP3Snapshot](get-hp3snapshot.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing HPE 3PAR StoreServ Storage Snapshot

|  |  |
| --- | --- |
| This example shows how to remove the HPE 3PAR StoreServ storage snapshot.  |  | | --- | | $snapshot = Get-HP3Snapshot -Name "vol1\_SS\_1"  Remove-HP3Snapshot -Snapshot $snapshot |  Perform the following steps:   1. Run the [Get-HP3Snapshot](get-hp3snapshot.md) cmdlet. Specify the Name parameter value. Save the result to the $snapshot variable. 2. Run the Remove-HP3Snapshot cmdlet. Set the $snapshot variable as the Snapshot parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Snapshots of Several HPE 3PAR StoreServ Storage Volumes

|  |  |
| --- | --- |
| This example shows how to remove snapshots of several HPE 3PAR StoreServ storage volumes.  |  | | --- | | $storage = Get-HP3Storage -Name "HPE 3PAR StoreServ"  $volume1 = Get-HP3Volume -Host $storage -Name "VOL01"  $volume2 = Get-HP3Volume -Host $storage -Name "VOL02"  $snapshot = Get-HP3Snapshot -Volume $volume1, $volume2  Remove-HP3Snapshot -Snapshot $snapshot |  Perform the following steps:   1. Get the volume snapshots you want to remove:  * Run the [Get-HP3Snapshot](get-hp3snapshot.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable. * Run the [Get-HP3Volume](get-hp3volume.md) cmdlet. Set the $storage variable as the Host parameter value. Save each volume to a separate variable: $volume1, $volume2, etc. * Run the [Get-HP3Snapshot](get-hp3snapshot.md) cmdlet. Set the $volume1 and $volume2 variables as the Volume parameter values. Save the result to the $snapshot variable.  1. Run the Remove-HP3Snapshot cmdlet. Set the $snapshot variable as the Snapshot parameter value. |

Related Commands

* [Get-HP3Storage](get-hp3storage.md)
* [Get-HP3Volume](get-hp3volume.md)
* [Get-HP3Snapshot](get-hp3snapshot.md)

Page updated 3/4/2024

Page content applies to build 13.0.1.1071
