---
title: "Get-VBRHvProxy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrhvproxy.html"
last_updated: "4/18/2024"
product_version: "13.0.1.1071"
---

# Get-VBRHvProxy


Short Description

Returns a list of the Hyper-V backup proxies.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRHvProxy [-Name <String[]>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns a list of the Hyper-V backup proxies added to the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of names of the Hyper-V proxies. The cmdlet will return proxies with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CHvProxy[] that contains an array of Hyper-V backup proxy servers added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting List of Hyper-V Backup Proxies

|  |  |
| --- | --- |
| This commands gets the list of all the Hyper-V proxies added to the backup infrastructure.  |  | | --- | | Get-VBRHvProxy | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting Hyper-V Backup Proxy by Name

|  |  |
| --- | --- |
| This command gets the Hyper-V backup proxy with the name LocalProxy.  |  | | --- | | Get-VBRHvProxy -Name "LocalProxy" | |


