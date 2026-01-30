---
title: "Get-HP3Volume"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-hp3volume.html"
last_updated: "2/6/2024"
product_version: "13.0.1.1071"
---

# Get-HP3Volume


Short Description

Returns HPE 3PAR StoreServ storage volumes added to the backup infrastructure.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: HPE 3PAR StoreServ

Syntax

|  |
| --- |
| Get-HP3Volume -Storage <CHp3PARHost[]> [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns HPE 3PAR StoreServ storage volumes added to the backup infrastructure.

|  |
| --- |
| ![Get-HP3Volume](images/icon_tip.webp) Tip: |
| Run the [Get-HP3InfrastructureVolume](get-hp3infrastructurevolume.md) cmdlet to get an array of volumes from HPE 3PAR StoreServ storage systems. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Storage | Specifies an array of storage systems. The cmdlet will return volumes of these storage systems. | Accepts the CHp3PARHost[] object. To get this object, run the [Get-HP3Storage](get-hp3storage.md) cmdlet. | False | Named | False |
| Name | Specifies an array of volume names. The cmdlet will return volumes with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

Getting HPE 3PAR StoreServ Volume

This example shows how to get an HPE 3PAR StoreServ volume added to the backup infrastructure.

|  |
| --- |
| $storage = Get-HP3Storage -Name "HPE 3PAR StoreServe Storage"  Get-HP3Volume -Storage $storage |

Perform the following steps:

1. Run the [Get-HP3Storage](get-hp3storage.md) cmdlet. Specify the Name parameter value. Save the result to the $storage variable.
2. Run the Get-HP3Volume cmdlet. Set the $storage variable as the Storage parameter value.

Related Commands

[Get-HP3Storage](get-hp3storage.md)


