---
title: "Get-NimbleVolume"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-nimblevolume.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Get-NimbleVolume

In this article

Short Description

Returns HPE Nimble volumes added to the backup infrastructure.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-NimbleVolume [-Name <string[]>] [-Host <CNimbleHost[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns HPE Nimble volumes added to the backup infrastructure.

|  |
| --- |
| ![Get-NimbleVolume](images/icon_tip.webp) Tip: |
| Run the [Get-NimbleInfrastructureVolume](get-nimbleinfrastructurevolume.md) cmdlet to get an array of volumes from HPE Nimble storage systems. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of volume names. The cmdlet will return volumes with these names. | String[] | False | Named | False |
| Host | Specifies an array of storage systems. The cmdlet will return volumes of these storage systems. | Accepts the CNimbleHost[] object. To get this object, run the [Get-NimbleHost](get-nimblehost.md) cmdlet. | False | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Getting HPE Nimble Volume

This example shows how to get an HPE Nimble volume added to the backup infrastructure.

|  |
| --- |
| $storage = Get-NimbleHost -Name "HPE Nimble-FC"  Get-NimbleVolume -Name "VOL01" -Host $storage |

Perform the following steps:

1. Run the [Get-NimbleHost](get-nimblehost.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Get-NimbleVolume cmdlet. Specify the Name parameter value. Set the $storage variable as the Host parameter value.

Related Commands

[Get-NimbleHost](get-nimblehost.md)

Page updated 2/16/2024

Page content applies to build 13.0.1.1071
