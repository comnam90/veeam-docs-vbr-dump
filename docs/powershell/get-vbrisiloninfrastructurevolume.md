---
title: "Get-VBRIsilonInfrastructureVolume"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrisiloninfrastructurevolume.html"
last_updated: "2/19/2024"
product_version: "13.0.1.1071"
---

# Get-VBRIsilonInfrastructureVolume


Short Description

Returns volumes of Dell PowerScale (formerly Isilon) storage systems.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRIsilonInfrastructureVolume [-Name <string[]>] [-Host <CIsilonHost>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of volumes of Dell PowerScale storage systems. The cmdlet will return storage volumes even if they are not added to your backup infrastructure.

|  |
| --- |
| ![Get-VBRIsilonInfrastructureVolume](images/icon_tip.webp) Tip: |
| You can use this cmdlet to specify storage volumes that you want to rescan or exclude from the storage rescan. |

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of volume names that you want to get. The cmdlet will return volumes with these names. | String | False | Named | False |
| Host | Specifies a storage. The cmdlet will return an array of volumes added to that storage system. | Accepts the CIsilonHost object. To create this object, run the [Get-VBRIsilonHost](get-vbrisilonhost.md) cmdlet. | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All Dell PowerScale Volumes

|  |  |
| --- | --- |
| This command returns all volumes added to Dell PowerScale storage systems.  |  | | --- | | Get-VBRIsilonInfrastructureVolume | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Dell PowerScale Volumes by Name

|  |  |
| --- | --- |
| This command returns Dell PowerScale storage volumes by the volume name.  |  | | --- | | Get-VBRIsilonInfrastructureVolume -Name "Volume4", "Volume5" | |


