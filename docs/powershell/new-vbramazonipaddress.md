---
title: "New-VBRAmazonIpAddress"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbramazonipaddress.html"
last_updated: "8/26/2025"
product_version: "13.0.1.1071"
---

# New-VBRAmazonIpAddress

In this article

Short Description

Defines settings of a private IP address for Amazon EC2 instances.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRAmazonIpAddress -Type {Dynamic | Static} [-Ip <string>] [<CommonParameters>] |

Detailed Description

This cmdlet defines settings for a private IP address that will be used during restore to Amazon EC2.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Type | Specifies type of a private IP address. You can set the following types:   * Dynamic: use this option to define a private dynamic IP address. * Static: use this option to define a private static IP address. | [VBRAmazonIpAddressType](enums.md#VBRAmazonIpAddressType) | True | Named | False |
| Ip | Used if Type is set to Static.  Specifies a private static IP address. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRAmazonIpAddress](vbramazonipaddress.md)

Examples

Defining Static IP Address

This command defines a static IP address.

|  |
| --- |
| New-VBRAmazonIpAddress -Type Static -Ip "172.172.72.72" |

Page updated 8/26/2025

Page content applies to build 13.0.1.1071
