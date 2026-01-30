---
title: "Remove-NimbleSnapshot"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-nimblesnapshot.html"
last_updated: "4/19/2024"
product_version: "13.0.1.1071"
---

# Remove-NimbleSnapshot


Short Description

Removes HPE Nimble storage snapshots.

|  |
| --- |
| Note |
| If the four-eyes authorization is enabled, you cannot run this cmdlet. For more information, see the [Four-Eyes Authorization](https://helpcenter.veeam.com/docs/vbr/userguide/four_eyes_authorization.html?ver=13) section in the User Guide for VMware vSphere. |

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-NimbleSnapshot -Snapshot <CSanSnapshot[]>  [<CommonParameters>] |

Detailed Description

This cmdlet permanently removes a selected HPE Nimble storage snapshot from your virtual infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Snapshot | Specifies the array of snapshots. The cmdlet will remove these snapshots. | Accepts the CSanSnapshot[] object. To get this object, run the [Get-NimbleSnapshot](get-nimblesnapshot.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Remove Snapshots of Several HPE Nimble Storage Volumes

This example shows how to remove snapshots of several HPE Nimble storage volumes.

|  |
| --- |
| $storage = Get-NimbleHost -Name "HPE Nimble-FC"  $volume1 = Get-NimbleVolume -Host $storage -Name "VOL01"  $volume2 = Get-NimbleVolume -Host $storage -Name "VOL02"  $snapshot = Get-NimbleSnapshot -Volume $volume1, $volume2  Remove-NimbleSnapshot -Snapshot $snapshot |

Perform the following steps:

1. Get the volume snapshots you want to remove.

* Run the [Get-NimbleHost](get-nimblehost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
* Run the [Get-NimbleVolume](get-nimblevolume.md) cmdlet. Set the $storage variable as the Host parameter value. Save each volume to a separate variable: $volume1, $volume2, etc.
* Run the [Get-NimbleSnapshot](get-nimblesnapshot.md) cmdlet. Set the $volume1 and $volume2 variables as the Volume parameter values. Save the result to the $snapshot variable.

1. Run the Remove-NimbleSnapshot cmdlet. Set the $snapshot variable as the Snapshot parameter value.

Related Commands

* [Get-NimbleHost](get-nimblehost.md)
* [Get-NimbleVolume](get-nimblevolume.md)
* [Get-NimbleSnapshot](get-nimblesnapshot.md)


