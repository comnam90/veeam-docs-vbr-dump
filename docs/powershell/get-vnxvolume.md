---
title: "Get-VNXVolume"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vnxvolume.html"
last_updated: "2/12/2024"
product_version: "13.0.1.1071"
---

# Get-VNXVolume

In this article

Short Description

Returns Dell VNX volumes added to the backup infrastructure.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: Dell VNX

Syntax

|  |
| --- |
| Get-VNXVolume [-Name <string[]>] [-Host <CVnxHost[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns Dell VNX volumes added to the backup infrastructure.

|  |
| --- |
| ![Get-VNXVolume](images/icon_tip.webp) Tip: |
| Run the [Get-VNXInfrastructureVolume](get-vnxinfrastructurevolume.md) cmdlet to get an array of volumes from Dell VNX storage systems. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of volume names. The cmdlet will return volumes with these names. | String[] | False | Named | False |
| Host | Specifies an array of storage systems. The cmdlet will return volumes of these storage systems. | Accepts the CVnxHost[] object. To get this object, run the [Get-VNXHost](get-vnxhost.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Getting Dell VNX Volume

This example shows how to get a Dell VNX volume added to the backup infrastructure.

|  |
| --- |
| $storage = Get-VNXHost -Name "VNX Storage"  Get-VNXVolume -Name "VOLUME1" -Host $storage |

Perform the following steps:

1. Run the [Get-VNXHost](get-vnxhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Get-VNXVolume cmdlet. Specify the Name parameter value. Set the $storage variable as the Host parameter value.

Related Commands

[Get-VNXHost](get-vnxhost.md)

Page updated 2/12/2024

Page content applies to build 13.0.1.1071
