---
title: "Get-VBRIsilonHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrisilonhost.html"
last_updated: "3/4/2024"
product_version: "13.0.1.1071"
---

# Get-VBRIsilonHost

In this article

Short Description

Returns Dell PowerScale (formerly Isilon) storage systems.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRIsilonHost [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

You can get the list of all Dell PowerScale storage systems added to your virtual infrastructure or narrow down the output by storage name.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of storage names. The cmdlet will return storage systems with these names. | String | False | Named | False |

<CommonParameters>

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Returning All Dell PowerScale Storage Systems

|  |  |
| --- | --- |
| This command returns all Dell PowerScale storage systems.  |  | | --- | | Get-VBRIsilonHost | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Returning Dell PowerScale Storage Systems by Name

|  |  |
| --- | --- |
| This command returns a Dell PowerScale storage by name.  |  | | --- | | Get-VBRIsilonHost -Name "Isilon Storage" | |

Page updated 3/4/2024

Page content applies to build 13.0.1.1071
