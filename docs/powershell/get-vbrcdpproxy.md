---
title: "Get-VBRCDPProxy"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrcdpproxy.html"
last_updated: "10/16/2025"
product_version: "13.0.1.1071"
---

# Get-VBRCDPProxy

In this article

Short Description

Returns CDP proxies added to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Get a CDP proxy by its name.

|  |
| --- |
| Get-VBRCDPProxy [-Name <string[]>]  [<CommonParameters>] |

* Get a CDP proxy by its ID.

|  |
| --- |
| Get-VBRCDPProxy [-Id <guid[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns CDP proxies added to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names for CDP proxies. The cmdlet will return a list of proxies with these names. | String[] | False | Named | True (ByValue, ByPropertyName) |
| Id | Specifies an array of Ids for CDP proxies. The cmdlet will return a list of proxies with these names IDs. | Guid[] | False | Named | True (ByValue, ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRCDPProxy object that contains CDP proxies to the backup infrastructure settings.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting CDP Proxy by Name

|  |  |
| --- | --- |
| This command returns the Proxy05 CDP Proxy.  |  | | --- | | Get-VBRCDPProxy -Name "Proxy05" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting CDP Proxy by ID

|  |  |
| --- | --- |
| This command returns the d602b38b-fab6-4c4e-8066-a1bf16affa76 CDP Proxy.  |  | | --- | | Get-VBRCDPProxy -Id "d602b38b-fab6-4c4e-8066-a1bf16affa76" | |

Page updated 10/16/2025

Page content applies to build 13.0.1.1071
