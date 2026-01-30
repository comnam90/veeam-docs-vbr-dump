---
title: "Add-NetAppSnapshot"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-netappsnapshot.html"
last_updated: "5/12/2025"
product_version: "13.0.1.1071"
---

# Add-NetAppSnapshot


Short Description

Creates NetApp storage snapshots.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-NetAppSnapshot -Volume <CSanVolume> [-Name <String>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a snapshot of a selected NetApp storage volume.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Volume | Specifies the storage volume for which you want to take snapshot. | Accepts the CSanVolume object. To get this object, run the [Get-NetAppVolume](get-netappvolume.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| Name | Specifies the name you want to assign to the snapshot. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Creating Snapshot of Specific Volume

This example shows how to create a snapshot of the Vol 01 volume.

|  |
| --- |
| $apphost = Get-NetAppHost -Name "NetApp Store"  Get-NetAppVolume -Host $apphost -Name "Vol 01" | Add-NetAppSnapshot -Name "vol\_SS\_01" |

Perform the following steps:

1. Run the [Get-NetAppHost](get-netapphost.md) cmdlet. Specify the Name parameter value. Save the result to the $apphost variable.
2. Run the [Get-NetAppVolume](get-netappvolume.md) cmdlet. Set the $apphost variable as the Host parameter value. Specify the Name parameter value.
3. Pipe the cmdlet output to the Add-NetAppSnapshot cmdlet. Specify the Name parameter value.

Related Commands

[Get-NetAppVolume](get-netappvolume.md)


