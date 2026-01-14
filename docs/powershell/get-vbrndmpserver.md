---
title: "Get-VBRNDMPServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrndmpserver.html"
last_updated: "2/2/2024"
product_version: "13.0.1.1071"
---

# Get-VBRNDMPServer

In this article

Short Description

Returns NDMP servers.

Applies to

Product Edition: Enterprise

Requires Cloud Connect license

Syntax

This cmdlet provides parameter sets that allow you to:

* Get an NDMP server by the NDMP server DNS or IP.

|  |
| --- |
| Get-VBRNDMPServer [-Name <string[]>]  [<CommonParameters>] |

* Get an NDMP server by the NDMP server ID.

|  |
| --- |
| Get-VBRNDMPServer -Id <guid[]>  [<CommonParameters>] |

Detailed Description

This cmdlet returns an array of NDMP servers managed by Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Id | Specifies an array of IDs for NDMP servers. The cmdlet will return NDMP servers with these IDs. | Guid[] | True | Named | False |
| Name | Specifies an array of DNS names or IP addresses of NDMP servers. The cmdlet will return NDMP servers with these DNS names or IP addresses. | String[] | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRNDMPServer](vbrndmpserver.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Getting NDMP Server by DNS Name

|  |  |
| --- | --- |
| This command gets the NetApp.tech.local NDMP server.  |  | | --- | | Get-VBRNDMPServer -Name "NetApp.tech.local" | |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Getting NDMP Server by Server ID

|  |  |
| --- | --- |
| This command gets the 0fccf7c9-1f90-49de-8bec-53a0697e04ab NDMP server.  |  | | --- | | Get-VBRNDMPServer -ID "0fccf7c9-1f90-49de-8bec-53a0697e04ab" | |

Page updated 2/2/2024

Page content applies to build 13.0.1.1071
