---
title: "Remove-VBRHvProxy"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrhvproxy.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Remove-VBRHvProxy


Short Description

Removes the Hyper-V backup proxy from the backup infrastructure.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Remove-VBRHvProxy -Proxy <CHvProxy[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet allows you to remove the specified Hyper-V backup proxy from the backup infrastructure.

When you remove a backup proxy, Veeam Backup & Replication unassigns the proxy role from the server, so it is no longer used as a backup proxy. The actual server remains added to the backup infrastructure.

|  |
| --- |
| Note: |
| You cannot remove a backup proxy that is explicitly selected in any backup, replication or VM copy job. To remove such a proxy, you need to delete all job references to it first. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Proxy | Specifies an array of the Hyper-V proxies you want to remove. | Accepts the CHvProxy[] object. To get this object, run the [Get-VBRHvProxy](get-vbrhvproxy.md) cmdlet. | True | Named | True (ByValue, |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Removing Hyper-V Backup Proxy [Using Variable]

|  |  |
| --- | --- |
| This example shows how to remove the Hyper-V backup proxy named LocalProxy.  |  | | --- | | $proxy = Get-VBRHvProxy -Name "LocalProxy"  Remove-VBRHvProxy -Proxy $proxy |  Perform the following steps:   1. Run the [Get-VBRHvProxy](get-vbrhvproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable. 2. Run the Remove-VBRHvProxy cmdlet. Set the $proxy variable as the Proxy parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Removing Hyper-V Backup Proxy [Using Pipeline]

|  |  |
| --- | --- |
| This example shows how to remove the Hyper-V backup proxy named LocalProxy.  |  | | --- | | Get-VBRHvProxy -Name "LocalProxy"| Remove-VBRHvProxy |  Perform the following steps:   1. Run the [Get-VBRHvProxy](get-vbrhvproxy.md) cmdlet. Specify the Name parameter value. Save the result to the $proxy variable. 2. Pipe the cmdlet output to the Remove-VBRHvProxy cmdlet. |

Related Commands

[Get-VBRHvProxy](get-vbrhvproxy.md)


