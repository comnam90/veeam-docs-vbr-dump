---
title: "Get-VNXHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vnxhost.html"
last_updated: "7/16/2025"
product_version: "13.0.1.1071"
---

# Get-VNXHost

In this article

Short Description

Returns Dell VNX storage systems.

Applies to

Platform: VMware

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Storage System: Dell VNX

Syntax

|  |
| --- |
| Get-VNXHost [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

You can get the list of all Dell VNX storage systems added to your virtual infrastructure or narrow down the output by storage name.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies the array of storage names. The cmdlet will return storage systems with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Returning All Dell VNX Storage Systems

|  |  |
| --- | --- |
| This command returns all Dell VNX storage systems.  |  | | --- | | Get-VNXHost | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Returning Dell VNX Storage System by Name

|  |  |
| --- | --- |
| This command returns a Dell VNX storage by name.  |  | | --- | | Get-VNXHost -Name "VNX Storage" | |

Page updated 7/16/2025

Page content applies to build 13.0.1.1071
