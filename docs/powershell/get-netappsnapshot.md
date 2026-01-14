---
title: "Get-NetAppSnapshot"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-netappsnapshot.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Get-NetAppSnapshot

In this article

Short Description

Returns NetApp storage snapshots.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-NetAppSnapshot [-Name <String[]>] [-Volume <CSanVolume[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns existing NetApp storage snapshots.

You can get the list of all storage snapshots, or look for a specific snapshot by name or associated volume.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of the snapshot names. The cmdlet will return the snapshots with these names. | String[] | False | Named | False |
| Volume | Specifies the array of volumes. The cmdlet will return the snapshots of these volumes. | Accepts the CSanVolume[] object. To get this object, run the [Get-NetAppVolume](get-netappvolume.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting Volumes of All NetApp Storage Systems

|  |  |
| --- | --- |
| This command returns the list of all snapshots.  |  | | --- | | Get-NetAppSnapshot | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Volumes of All NetApp Storage Systems

|  |  |
| --- | --- |
| This example shows how to get snapshots of a specific volume.  |  | | --- | | $vol = Get-NetAppVolume | Select -last 1  Get-NetAppSnapshot -Volume $vol |  Perform the following steps:   1. Run the [Get-NetAppVolume](get-netappvolume.md) cmdlet. Select the last volume in the list. Save the result to the $vol variable. 2. Run the Get-NetAppSnapshot cmdlet. Set the $vol variable as the Volume parameter value. |

Related Commands

[Get-NetAppVolume](get-netappvolume.md)

Page updated 5/12/2025

Page content applies to build 13.0.1.1071
