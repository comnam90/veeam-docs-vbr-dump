---
title: "Get-VBRIsilonVolume"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrisilonvolume.html"
last_updated: "2/5/2024"
product_version: "13.0.1.1071"
---

# Get-VBRIsilonVolume

In this article

Short Description

Returns Dell PowerScale (formerly Isilon) volumes added to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRIsilonVolume [-Name <string[]>] [-Host <CIsilonHost[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Dell PowerScale volumes added to the backup infrastructure.

|  |
| --- |
| ![Get-VBRIsilonVolume](images/icon_tip.webp) Tip: |
| Run the [Get-VBRIsilonInfrastructureVolume](get-vbrisiloninfrastructurevolume.md) cmdlet to get an array of volumes from Dell PowerScale storage systems. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of volume names that you want to get. The cmdlet will return volumes with these names. | String | False | Named | False |
| Host | Specifies a storage. The cmdlet will return an array of volumes added to that storage system. | Accepts the CIsilonHost object. To create this object, run the [Get-VBRIsilonHost](get-vbrisilonhost.md) cmdlet. | False | Named | True ByValue, ByPropertyName |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Getting Dell PowerScale Volume Added to Backup Infrastructure

This example shows how to get a Dell PowerScale volume added to the backup infrastructure.

|  |
| --- |
| $storage = Get-VBRIsilonHost -Name "Isilon Storage"  Get-VNXVolume -Name "VOLUME1" -Host $storage |

Perform the following steps:

1. Run the [Get-VBRIsilonHost](get-vbrisilonhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Get-VBRIsilonVolume cmdlet. Specify the Name parameter value. Set the $storage variable as the Host parameter value.

Related Commands

[Get-VBRIsilonHost](get-vbrisilonhost.md)

Page updated 2/5/2024

Page content applies to build 13.0.1.1071
