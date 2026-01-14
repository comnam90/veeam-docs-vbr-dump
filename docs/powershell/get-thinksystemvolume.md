---
title: "Get-ThinkSystemVolume"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-thinksystemvolume.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Get-ThinkSystemVolume

In this article

Short Description

Returns ThinkSystem storage volumes added to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-ThinkSystemVolume [-Name <string[]>] [-Host <CNaHost[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns ThinkSystem storage volumes added to the backup infrastructure.

|  |
| --- |
| ![Get-ThinkSystemVolume](images/icon_tip.webp) Tip: |
| Run the [Get-NetAppInfrastructureVolume](get-netappinfrastructurevolume.md) cmdlet to get an array of volumes from a ThinkSystem storage system. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of volume names. The cmdlet will return volumes with these names. | String | False | Named | False |
| Host | Specifies an array of storage systems. The cmdlet will return volumes of these storage systems. | Accepts the CNaHost object. To create this object, run the [Get-ThinkSystemHost](get-thinksystemhost.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Getting ThinkSystem Storage Volume

This example shows how to get a specific ThinkSystem storage volume added to the backup infrastructure.

|  |
| --- |
| $storage = Get-ThinkSystemHost -Name "ThinkSystem Store"  Get-ThinkSystemVolume -Name "ThinkSystem Volume 01" -Host $storage |

Perform the following steps:

1. Run the [Get-ThinkSystemHost](get-thinksystemhost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Get-ThinkSystemVolume cmdlet. Specify the Name parameter value. Set the $storage variable as the Host parameter value.

Related Commands

[Get-ThinkSystemHost](get-thinksystemhost.md)

Page updated 2/16/2024

Page content applies to build 13.0.1.1071
