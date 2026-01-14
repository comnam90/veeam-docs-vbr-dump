---
title: "Get-HyperFlexHost"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-hyperflexhost.html"
last_updated: "8/14/2024"
product_version: "13.0.1.1071"
---

# Get-HyperFlexHost

In this article

Short Description

Returns Cisco HyperFlex storage systems.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-HyperFlexHost [-Name <string[]>]  [<CommonParameters>] |

Detailed Description

You can get the list of all Cisco HyperFlex storage systems added to your backup infrastructure or narrow down the output by storage name.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Name | Specifies an array of storage names. The cmdlet will return storage systems with these names. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the CCiscoHxHost object that defines settings of the HyperFlex storage systems added to the backup infrastructure.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Returning All Cisco HyperFlex Storage Systems

|  |  |
| --- | --- |
| This command returns all Cisco HyperFlex storage systems.  |  | | --- | | Get-HyperFlexHost | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Returning Cisco HyperFlex Storage Systems by Name

|  |  |
| --- | --- |
| This command returns the HX Storage Cisco HyperFlex storage.  |  | | --- | | Get-HyperFlexHost -Name "HX Storage" | |

Page updated 8/14/2024

Page content applies to build 13.0.1.1071
