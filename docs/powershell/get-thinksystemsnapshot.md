---
title: "Get-ThinkSystemSnapshot"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-thinksystemsnapshot.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Get-ThinkSystemSnapshot

In this article

Short Description

Returns ThinkSystem storage snapshots.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-ThinkSystemSnapshot [-Name <string[]>] [-Volume <CSanVolume[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns existing ThinkSystem storage snapshots.

You can get the list of all storage snapshots, or look for a specific snapshot by name or associated volume.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of the snapshot names. The cmdlet will return the snapshots with these names. | String | False | Named | False |
| Volume | Specifies the array of volumes. The cmdlet will return the snapshots of these volumes. | Accepts the CSanVolume object. To create this object, run the [Get-ThinkSystemVolume](get-thinksystemvolume.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Snapshots

|  |  |
| --- | --- |
| This command returns the list of all snapshots.  |  | | --- | | Get-ThinkSystemSnapshot | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Snapshots of Specific Volume

|  |  |
| --- | --- |
| This example shows how to get snapshots of a specific volume.  |  | | --- | | $vol = Get-ThinkSystemVolume | Select -last 1  Get-ThinkSystemSnapshot -Volume $vol |  Perform the following steps:   1. Run the [Get-ThinkSystemVolume](get-thinksystemvolume.md) cmdlet. Select the last volume in the list. Save the result to the $vol variable. 2. Run the Get-ThinkSystemSnapshot cmdlet. Set the $vol variable as the Volume parameter value. |

Related Commands

[Get-ThinkSystemVolume](get-thinksystemvolume.md)

Page updated 2/16/2024

Page content applies to build 13.0.1.1071
