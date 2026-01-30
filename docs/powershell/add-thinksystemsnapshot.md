---
title: "Add-ThinkSystemSnapshot"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-thinksystemsnapshot.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Add-ThinkSystemSnapshot


Short Description

Creates ThinkSystem storage snapshots.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-ThinkSystemSnapshot -Volume <CSanVolume> [-Name <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a snapshot of a selected ThinkSystem storage volume.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Volume | Specifies the storage volume for which you want to take snapshot. | Accepts the CSanVolume object. To create this object, run the [Get-ThinkSystemVolume](get-thinksystemvolume.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the name you want to assign to the snapshot. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Creating Snapshot

This example shows how to create a snapshot of a volume.

|  |
| --- |
| $apphost = Get-ThinkSystemHost -Name "ThinkSystem Store"  $volume = Get-ThinkSystemVolume -Host $apphost -Name "Vol 01"  Add-ThinkSystemSnapshot -Volume $volume -Name "vol\_SS\_01" |

Perform the following steps:

1. Run the [Add-ThinkSystemHost](add-thinksystemhost.md) cmdlet. Specify the Name parameter value. Save the result to the $apphost variable.
2. Run the [Get-ThinkSystemVolume](get-thinksystemvolume.md) cmdlet. Specify the Name and Host parameter values. Save the result to the $volume variable.
3. Run the Add-ThinkSystemSnapshot cmdlet. Set the $volume variable as the Volume parameter value. Specify the Name parameter value.

Related Commands

* [Add-ThinkSystemHost](add-thinksystemhost.md)
* [Get-ThinkSystemVolume](get-thinksystemvolume.md)


