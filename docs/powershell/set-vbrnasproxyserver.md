---
title: "Set-VBRNASProxyServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrnasproxyserver.html"
last_updated: "5/26/2025"
product_version: "13.0.1.1071"
---

# Set-VBRNASProxyServer

In this article

Short Description

Modifies the general-purpose backup proxy added to the Veeam Backup & Replication infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRNASProxyServer -ProxyServer <VBRNASProxyServer> [-Description <string>] [-ConcurrentTaskNumber <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of the general-purpose backup proxy added to the Veeam Backup & Replication infrastructure.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ProxyServer | Specifies the general-purpose backup proxy. The cmdlet will modify the settings of this proxy. | Accepts the VBRNASProxyServer object. To get this object, run the [Get-VBRNASProxyServer](get-vbrnasproxyserver.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Description | Specifies a description of the general-purpose backup proxy. The cmdlet will add the proxy with the specified description. | String | False | Named | False |
| ConcurrentTaskNumber | Specifies the number of concurrent tasks that can be assigned to the general-purpose backup proxy simultaneously.  Permitted values: 1-100. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRNASProxyServer](vbrnasproxyserver.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Description

|  |  |
| --- | --- |
| This example shows how to modify a description of the general-purpose backup proxy.  |  | | --- | | $proxy = Get-VBRNASProxyServer -Name "Proxy05"  Set-VBRNASProxyServer -ProxyServer $proxy -Description "Proxy for SMB network shared folders" |  Perform the following steps:   1. Run the [Get-VBRNASProxyServer](get-vbrnasproxyserver.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable. 2. Run the Set-VBRNASProxyServer cmdlet. Set the $proxy variable as the ProxyServer parameter value. Specify the Description parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Number of Concurrent Tasks

|  |  |
| --- | --- |
| This example shows how to modify the number of concurrent tasks for the general-purpose backup proxy. The general-purpose backup proxy will process 50 concurrent tasks simultaneously.  |  | | --- | | $proxy = Get-VBRNASProxyServer -Name "Proxy05"  Set-VBRNASProxyServer -ProxyServer $proxy -ConcurrentTaskNumber 50 |  Perform the following steps:   1. Run the [Get-VBRNASProxyServer](get-vbrnasproxyserver.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable. 2. Run the Set-VBRNASProxyServer cmdlet. Set the $proxy variable as the ProxyServer parameter value. Specify the ConcurrentTaskNumber parameter value. |

Related Commands

[Get-VBRNASProxyServer](get-vbrnasproxyserver.md)

Page updated 5/26/2025

Page content applies to build 13.0.1.1071
