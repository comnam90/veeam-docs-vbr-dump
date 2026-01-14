---
title: "Remove-VBRNASProxyServer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrnasproxyserver.html"
last_updated: "5/26/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRNASProxyServer

In this article

Short Description

Removes general-purpose backup proxies from the Veeam Backup & Replication infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRNASProxyServer -ProxyServer <VBRNASProxyServer[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes general-purpose backup proxies from the Veeam Backup & Replication infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ProxyServer | Specifies an array of general-purpose backup proxies. The cmdlet will remove these proxies from the Veeam Backup & Replication infrastructure. | Accepts the VBRNASProxyServer[] object. To get this object, run the [Get-VBRNASProxyServer](get-vbrnasproxyserver.md) cmdlet. |  |  |  |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if the user is sure that he wants to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing General-Purpose Backup Proxy

This example shows how to remove the File Server Proxy general-purpose backup proxy from the Veeam Backup & Replication infrastructure.

|  |
| --- |
| $proxy = Get-VBRNASProxyServer -Name "File Server Proxy"  Remove-VBRNASProxyServer -ProxyServer $proxy |

Perform the following steps:

1. Run the [Get-VBRNASProxyServer](get-vbrnasproxyserver.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable.
2. Run the Remove-VBRNASProxyServer cmdlet. Set the $proxy variable as the ProxyServer parameter value.

Related Commands

[Get-VBRNASProxyServer](get-vbrnasproxyserver.md)

Page updated 5/26/2025

Page content applies to build 13.0.1.1071
