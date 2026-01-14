---
title: "Get-VBRDiscoveredComputerUpdate"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrdiscoveredcomputerupdate.html"
last_updated: "1/3/2024"
product_version: "13.0.1.1071"
---

# Get-VBRDiscoveredComputerUpdate

In this article

Short Description

Returns available Veeam Agent private fixes.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRDiscoveredComputerUpdate [-Id <uint64>] [-AgentVersion <version>]  [<CommonParameters>] |

Detailed Description

This cmdlet returns the list of available Veeam Agent private fixes.

You can get all available private fixes or search for instances directly by the issue number or version.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies the issue number of the private fix. The cmdlet will return private fixes with this number. | Uint64 | False | Named | True (ByValue, ByProperty Name) |
| AgentVersion | Specifies the version of the private fix.  The cmdlet will return private fixes of this version. | Version | False | Named | True (ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRDiscoveredComputerUpdate[]](vbrdiscoveredcomputerupdate.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Returning All Available Private Fixes

|  |  |
| --- | --- |
| This command returns all available private fixes.  |  | | --- | | Get-VBRDiscoveredComputerUpdate | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Returning Private Fixes by Issue Number

|  |  |
| --- | --- |
| This command returns private fixes by the issue number.  |  | | --- | | Get-VBRDiscoveredComputerUpdate -Id 188235 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Returning Private Fixes by Version Number

|  |  |
| --- | --- |
| This command returns private fixes by the major and minor version numbers.  |  | | --- | | Get-VBRDiscoveredComputerUpdate -AgentVersion 2.1 | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Returning Private Fixes by Version, Build and Revision Numbers

|  |  |
| --- | --- |
| This command returns private fixes by the major and minor version numbers, the build number and the revision number.  |  | | --- | | Get-VBRDiscoveredComputerUpdate -AgentVersion 2.1.10.304 | |

Page updated 1/3/2024

Page content applies to build 13.0.1.1071
