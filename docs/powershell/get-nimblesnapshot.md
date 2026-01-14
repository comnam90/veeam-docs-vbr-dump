---
title: "Get-NimbleSnapshot"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-nimblesnapshot.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Get-NimbleSnapshot

In this article

Short Description

Returns HPE Nimble storage snapshots.

Applies to

Platform: VMware

Product Edition: Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-NimbleSnapshot [-Name <string[]>] [-Volume <CSanVolume[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns HPE Nimble storage snapshots.

You can get the list of all storage snapshots or look for a specific snapshot by name or associated volume.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of snapshot names. The cmdlet will return the snapshots with these names. | String[] | False | Named | False |
| Volume | Specifies the array of storage volumes. The cmdlet will return the snapshots of these volumes. | Accepts the CSanVolume[] object. To get this object, run the [Get-NimbleVolume](get-nimblevolume.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting HPE Nimble Storage Snapshot by Name

|  |  |
| --- | --- |
| This command returns an existing HPE Nimble storage snapshot by name.  |  | | --- | | Get-NimbleSnapshot -Name "DailySnapshot01" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Snapshots of Several HPE Nimble Storage Volumes

|  |  |
| --- | --- |
| This example shows how to get the existing snapshots of several HPE Nimble storage volumes.  |  | | --- | | $storage = Get-NimbleHost -Name "HPE Nimble-FC"  $volume1 = Get-NimbleVolume -Host $storage -Name "VOL01"  $volume2 = Get-NimbleVolume -Host $storage -Name "VOL02"  Get-NimbleSnapshot -Volume $volume1, $volume2 |  Perform the following steps:   1. Run the [Get-NimbleHost](get-nimblehost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable. 2. Run the [Get-NimbleVolume](get-nimblevolume.md) cmdlet. Set the $storage variable as the Host parameter value. Specify the Name parameter value. Save each volume to a separate variable: $volume1, $volume2, etc. 3. Run the Get-NimbleSnapshot cmdlet. Set the $volume1 and $volume2 variables as the Volume parameter values. |

Related Commands

* [Get-NimbleHost](get-nimblehost.md)
* [Get-NimbleVolume](get-nimblevolume.md)

Page updated 2/16/2024

Page content applies to build 13.0.1.1071
