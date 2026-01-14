---
title: "Add-NimbleSnapshot"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-nimblesnapshot.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Add-NimbleSnapshot

In this article

Short Description

Creates HPE Nimble storage snapshots.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-NimbleSnapshot -Volume <CSanVolume> [-Name <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a snapshot of a selected HPE Nimble storage volume.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Volume | Specifies the storage volume for which you want to take snapshot. | Accepts the CSanVolume object. To get this object, run the [Get-NimbleVolume](get-nimblevolume.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the name you want to assign to the snapshot. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Creating HPE Nimble Storage Snapshot

This example shows how to create a volume snapshot.

|  |
| --- |
| $storage = Get-NimbleHost -Name "HPE Nimble-FC"  $volume = Get-NimbleVolume -Host $storage -Name "VOL01"  Add-NimbleSnapshot -Volume $volume -Name "DailySnapshot01" |

Perform the following steps:

1. Run the [Get-NimbleHost](get-nimblehost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the [Get-NimbleVolume](get-nimblevolume.md) cmdlet. Set the $storage variable as the Host parameter value. Specify the Name parameter value. Save the result to the $volume variable.
3. Run the Add-NimbleSnapshot cmdlet. Set the $volume variable as the Volume parameter value. Specify the Name parameter value.

Related Commands

* [Get-NimbleHost](get-nimblehost.md)
* [Get-NimbleVolume](get-nimblevolume.md)

Page updated 2/16/2024

Page content applies to build 13.0.1.1071
