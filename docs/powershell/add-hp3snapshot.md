---
title: "Add-HP3Snapshot"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-hp3snapshot.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Add-HP3Snapshot

In this article

Short Description

Creates HPE 3PAR StoreServ storage snapshots.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: HPE 3PAR StoreServ

Syntax

|  |
| --- |
| Add-HP3Snapshot -Volume <CSanVolume> [-Name <string>] [-Description <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a snapshot of a selected HPE 3PAR StoreServ storage volume.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Volume | Specifies the storage volume for which you want to take snapshot. | Accepts the CSanVolume object. To get this object, run the [Get-HP3Volume](get-hp3volume.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the name you want to assign to the snapshot. | String | False | Named | False |
| Description | Specifies the description of the snapshot. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Creating Snapshot of HPE 3PAR StoreServ Storage Volume

This example shows how to create a snapshot of the HPE 3PAR StoreServ storage volume.

|  |
| --- |
| $storage = Get-HP3Storage -Name "HPE 3PAR StoreServe Storage"  $volume = Get-HP3Volume -Storage $storage  Add-HP3Snapshot -Volume $volume -Name "vol\_SS\_01" -Description "Vol 01 snapshot" |

Perform the following steps:

1. Run the [Get-HP3Storage](get-hp3storage.md) cmdlet. Specify the Name parameter value. Save it to the $storage variable.
2. Run the [Get-HP3Volume](get-hp3volume.md) cmdlet. Set the $storage variable as the Storage parameter value. Save the volume to the $volume variable.
3. Run the Add-HP3Snapshot cmdlet. Set the $volume variable as the Volume parameter value. Specify the Name parameter value. Specify the Description parameter value.

Related Commands

[Get-HP3Volume](get-hp3volume.md)

Page updated 2/16/2024

Page content applies to build 13.0.1.1071
