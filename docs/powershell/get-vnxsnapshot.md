---
title: "Get-VNXSnapshot"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vnxsnapshot.html"
last_updated: "2/12/2024"
product_version: "13.0.1.1071"
---

# Get-VNXSnapshot


Short Description

Returns Dell VNX storage snapshots.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: Dell VNX

Syntax

|  |
| --- |
| Get-VNXSnapshot [-Name <string[]>] [-Volume <CSanVolume[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns existing Dell VNX storage snapshots.

You can get the list of all storage snapshots, or look for a specific snapshot by name or associated volume.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of snapshot names. The cmdlet will return snapshots with these names. | String[] | False | Named | False |
| Volume | Specifies the array of storage volumes. The cmdlet will return snapshots of these volumes. | Accepts the CSanVolume[] object. To get this object, run the [Get-VNXVolume](get-vnxvolume.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Getting Snapshots of Dell VNX Storage Volume

This example shows how to get the existing snapshots of the Dell VNX storage volume.

|  |
| --- |
| $storage = Get-VNXHost -Name "VNX Storage"  $volume = Get-VNXVolume -Name "VOLUME1" -Host $storage  Get-VNXSnapshot -Volume $volume |

Perform the following steps:

1. Run the [Get-VNXHost](get-vnxhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the [Get-VNXVolume](get-vnxvolume.md) cmdlet. Specify the Name parameter value. Set the $storage variable as the Host parameter value. Save the result to the $volume variable.
3. Run the Get-VNXSnapshot cmdlet. Set the $volume variable as the Volume parameter value.

Related Commands

* [Get-VNXHost](get-vnxhost.md)
* [Get-VNXVolume](get-vnxvolume.md)


