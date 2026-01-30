---
title: "Remove-VBRCDPProxy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrcdpproxy.html"
last_updated: "10/16/2025"
product_version: "13.0.1.1071"
---

# Remove-VBRCDPProxy


Short Description

Removes CDP proxies from the backup infrastructure.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRCDPProxy -Proxy <VBRCDPProxy[]> [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes CDP proxies from the backup infrastructure.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Proxy | Specifies an array of CDP proxies. The cmdlet will remove these proxies from the backup infrastructure. | Accepts the VBRCDPProxy[] object. To create this object, run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| Force | Defines that the cmdlet will remove a CDP proxy without showing warnings in the PowerShell console. | SwitchParameter | False | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing CDP Proxies from Backup Infrastructure

This example shows how to remove several CDP Proxies from the backup infrastructure.

|  |
| --- |
| $proxy = Get-VBRCDPProxy  Remove-VBRCDPProxy -Proxy $proxy |

Perform the following steps:

1. Run the [Get-VBRCDPProxy](get-vbrcdpproxy.md) cmdlet. Save the result to the $proxy variable.
2. Run the Remove-VBRCDPProxy cmdlet. Set the $proxy variable as the Proxy parameter value.

Related Commands

[Get-VBRCDPProxy](get-vbrcdpproxy.md)


