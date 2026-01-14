---
title: "Add-VBRNASProxyServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/add-vbrnasproxyserver.html"
last_updated: "6/3/2025"
product_version: "13.0.1.1071"
---

# Add-VBRNASProxyServer

In this article

Short Description

Adds the general-purpose backup proxy to the Veeam Backup & Replication infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Add-VBRNASProxyServer -Server <CHost> [-Description <string>] [-ConcurrentTaskNumber <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet adds the general-purpose backup proxy to the Veeam Backup & Replication infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies the host where the general-purpose backup proxy is located. The cmdlet will add this host as the proxy server to the Veeam Backup & Replication infrastructure. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Description | Specifies a description of the general-purpose backup proxy. The cmdlet will add the proxy server with the specified description. | String | False | Named | False |
| ConcurrentTaskNumber | Specifies the number of concurrent tasks that can be assigned to the general-purpose backup proxy simultaneously.  Permitted values: 1-100.  Default: 2. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRNASProxyServer](vbrnasproxyserver.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Adding General-Purpose Backup Proxy

|  |  |
| --- | --- |
| This example shows how to add the general-purpose backup proxy to the Veeam Backup & Replication infrastructure. The general-purpose backup proxy is assigned two concurrent tasks to process.  |  | | --- | | $server = Get-VBRServer -Name "File Backup Proxy"  Add-VBRNASProxyServer -Server $server |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Add-VBRNASProxyServer cmdlet. Set the $server variable as the Server parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Adding General-Purpose Backup Proxy with Specific Number of Concurrent Tasks

|  |  |
| --- | --- |
| This example shows how to add the general-purpose backup proxy to the Veeam Backup & Replication infrastructure. The general-purpose backup proxy is assigned 100 concurrent tasks to process.  |  | | --- | | $server = Get-VBRServer -Name "File Backup Proxy"  Add-VBRNASProxyServer -Server $server -ConcurrentTaskNumber 100 |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the Add-VBRNASProxyServer cmdlet. Set the $server variable as the Server parameter value. Specify the ConcurrentTaskNumber parameter value. |

Related Commands

[Get-VBRServer](get-vbrserver.md)

Page updated 6/3/2025

Page content applies to build 13.0.1.1071
