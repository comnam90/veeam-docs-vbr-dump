---
title: "Enable-VBRComputerFileProxyServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrcomputerfileproxyserver.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# Enable-VBRComputerFileProxyServer


Short Description

Enables disabled general-purpose backup proxies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRComputerFileProxyServer -Proxy <VBRComputerFileProxyServer[]>  [<CommonParameters>] |

Detailed Description

This cmdlet enables disabled general-purpose backup proxies.

Run the [Disable-VBRComputerFileProxyServer](disable-vbrcomputerfileproxyserver.md) cmdlet to disable a general-purpose backup proxy.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Proxy | Specifies an array of general-purpose backup proxies. The cmdlet will enable these backup proxies. | Accepts the VBRComputerFileProxyServer[] object. To get this object, run the [Get-VBRComputerFileProxyServer](get-vbrcomputerfileproxyserver.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRComputerFileProxyServer object that contains settings of the general-purpose backup proxy added to the backup infrastructure.

Examples

Enabling Disabled General-purpose Backup Proxy

This example shows how to enable a disabled general-purpose backup proxy.

|  |
| --- |
| $fileproxy = Get-VBRComputerFileProxyServer  Enable-VBRComputerFileProxyServer -Proxy $fileproxy[3] |

Perform the following steps:

1. Run the [Get-VBRComputerFileProxyServer](get-vbrcomputerfileproxyserver.md) cmdlet. Save the result to the $fileproxy variable.
2. Run the Enable-VBRComputerFileProxyServer cmdlet. Set the $fileproxy variable as the Proxy parameter value.

The Get-VBRComputerFileProxyServer cmdlet will return an array of backup proxies. Mind the ordinal number of the necessary backup proxy (in our example, it is the fourth backup proxy in the array).

Related Commands

[Get-VBRComputerFileProxyServer](get-vbrcomputerfileproxyserver.md)


