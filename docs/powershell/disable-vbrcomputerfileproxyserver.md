---
title: "Disable-VBRComputerFileProxyServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/disable-vbrcomputerfileproxyserver.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# Disable-VBRComputerFileProxyServer

In this article

Short Description

Disables general-purpose backup proxies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Disable-VBRComputerFileProxyServer -Proxy <VBRComputerFileProxyServer[]>  [<CommonParameters>] |

Detailed Description

This cmdlet disables general-purpose backup proxies.

Run the [Enable-VBRComputerFileProxyServer](enable-vbrcomputerfileproxyserver.md) cmdlet to enable a file backup proxy.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Proxy | Specifies an array of general-purpose backup proxies. The cmdlet will disable these backup proxies. | Accepts the VBRComputerFileProxyServer[] object. To get this object, run the [Get-VBRComputerFileProxyServer](get-vbrcomputerfileproxyserver.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRComputerFileProxyServer object that contains settings of the general-purpose backup proxy added to the backup infrastructure.

Examples

Disabling General-purpose Backup Proxy

This example shows how to disable a general-purpose backup proxy.

|  |
| --- |
| $fileproxy = Get-VBRComputerFileProxyServer  Disable-VBRComputerFileProxyServer -Proxy $fileproxy[3] |

Perform the following steps:

1. Run the [Get-VBRComputerFileProxyServer](get-vbrcomputerfileproxyserver.md) cmdlet. Save the result to the $fileproxy variable.
2. Run the Disable-VBRComputerFileProxyServer cmdlet. Set the $fileproxy[3] variable as the Proxy parameter value.

The Get-VBRComputerFileProxyServer cmdlet will return an array of backup proxies. Mind the ordinal number of the necessary backup proxy (in our example, it is the fourth backup proxy in the array).

Related Commands

[Get-VBRComputerFileProxyServer](get-vbrcomputerfileproxyserver.md)

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
