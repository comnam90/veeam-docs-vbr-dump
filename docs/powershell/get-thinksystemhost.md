---
title: "Get-ThinkSystemHost"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-thinksystemhost.html"
last_updated: "2/16/2024"
product_version: "13.0.1.1071"
---

# Get-ThinkSystemHost


Short Description

Returns ThinkSystem storage systems added to the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-ThinkSystemHost [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns the list of all ThinkSystem storage systems added to the backup infrastructure or narrow down the output by a storage name.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of storage names. The cmdlet will return storage systems with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting All ThinkSystem Storage Systems

|  |  |
| --- | --- |
| This command returns all ThinkSystem storage systems.  |  | | --- | | Get-ThinkSystemHost | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting ThinkSystem Storage Systems by Name

|  |  |
| --- | --- |
| This command returns a ThinkSystem storage by name.  |  | | --- | | Get-ThinkSystemHost -Name "ThinkSystem Store" | |


