---
title: "Enable-VBRNASProxyServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrnasproxyserver.html"
last_updated: "5/26/2025"
product_version: "13.0.1.1071"
---

# Enable-VBRNASProxyServer


Short Description

Enables general-purpose backup proxies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRNASProxyServer -Proxy <VBRNASProxyServer[]>  [<CommonParameters>] |

Detailed Description

This cmdlet allows you to enable general-purpose backup proxies.

Run the [Disable-VBRNASProxyServer](disable-vbrnasproxyserver.md) cmdlet to disable general-purpose backup proxies.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Proxy | Specifies an array of general-purpose backup proxies you want to enable. | Accepts the VBRNASProxyServer[] object. To get this object, run the [Get-VBRNASProxyServer](get-vbrnasproxyserver.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Enabling General-Purpose Backup Proxy by Name

This example shows how to enable the File Share Backup Proxy 09 proxy.

|  |
| --- |
| $nasproxy = Get-VBRNASProxyServer -Name "File Backup Proxy 09"  Enable-VBRNASProxyServer -Proxy $nasproxy |

Perform the following steps:

1. Run the [Get-VBRNASProxyServer](get-vbrnasproxyserver.md) cmdlet. Specify the Name parameter value. Save the result to the $nasproxy variable.
2. Run the Enable-VBRNASProxyServer cmdlet. Set the $nasproxy variable as the Proxy parameter value.

Related Commands

[Get-VBRNASProxyServer](get-vbrnasproxyserver.md)


