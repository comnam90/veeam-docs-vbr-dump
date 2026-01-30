---
title: "Enable-VBRCDPProxy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/enable-vbrcdpproxy.html"
last_updated: "10/16/2025"
product_version: "13.0.1.1071"
---

# Enable-VBRCDPProxy


Short Description

Enables CDP proxies that were disabled.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Enable-VBRCDPProxy -Proxy <VBRCDPProxy[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet enables CDP proxies that were disabled.

Run the [Disable-VBRCDPProxy](disable-vbrcdpproxy.md) cmdlet to disable CDP proxies.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Proxy | Specifies an array of CDP proxies. The cmdlet will enable these proxies. | Accepts the VBRCDPProxy[] object. To create this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Enabling CDP Proxies

This example shows how to enable CDP proxies.

|  |
| --- |
| $proxy = Get-VBRCDPProxy  Enable-VBRCDPProxy -Proxy $proxy |

Perform the following steps:

1. Run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. Save the result to the $proxy variable.
2. Run the Enable-VBRCDPProxy cmdlet. Set the $proxy variable as the Proxy parameter value.

Related Commands

[Get-VBRCDPProxy](get-vbrcdpproxy.md)


