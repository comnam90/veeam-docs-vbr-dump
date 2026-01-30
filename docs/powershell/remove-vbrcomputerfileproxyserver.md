---
title: "Remove-VBRComputerFileProxyServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrcomputerfileproxyserver.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRComputerFileProxyServer


Short Description

Removes general-purpose backup proxies from the Veeam Backup & Replication infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRComputerFileProxyServer -ProxyServer <VBRComputerFileProxyServer[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes general-purpose backup proxies from the Veeam Backup & Replication infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ProxyServer | Specifies the general-purpose backup proxy. The cmdlet will remove this backup proxy from the Veeam Backup & Replication infrastructure. | Accepts the VBRComputerFileProxyServer object. To get this object, run the [Get-VBRComputerFileProxyServer](get-vbrcomputerfileproxyserver.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing General-purpose Backup Proxy

This example shows how to remove the File Proxy 01 file backup proxy from the Veeam Backup & Replication infrastructure.

|  |
| --- |
| $proxy = Get-VBRComputerFileProxyServer -Name "File Proxy 01"  Remove-VBRComputerFileProxyServer -FileProxy $proxy |

Perform the following steps:

1. Run the [Get-VBRComputerFileProxyServer](get-vbrcomputerfileproxyserver.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable.
2. Run the Remove-VBRComputerFileProxyServer cmdlet. Set the $proxy variable as the FileProxy parameter value.

Related Commands

[Get-VBRComputerFileProxyServer](get-vbrcomputerfileproxyserver.md)


