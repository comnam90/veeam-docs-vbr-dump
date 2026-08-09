---
title: "Remove-VBRNDMPServer"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/remove-vbrndmpserver.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Remove-VBRNDMPServer


Short Description

Removes NDMP and NetApp NDMP servers from the backup infrastructure.

Applies to

Product Edition: Enterprise

Requires Cloud Connect license

Syntax

|  |
| --- |
| Remove-VBRNDMPServer -Server <VBRNDMPServerBase[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes NDMP servers and NetApp NDMP servers from the backup infrastructure. When you remove the NDMP server from Veeam Backup & Replication you stop managing it via your Veeam Backup & Replication console. You do not delete the NDMP server itself as well as data stored on it, for example, the backup files.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| Server | Specifies the NDMP server that you want to remove. | Accepts the VBRNDMPServerBase[] object. To get this object, run the [Get-VBRNDMPServer](get-vbrndmpserver.md) cmdlet. | True | Named | False |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Removing NDMP Server from Backup Infrastructure

This example shows how to remove an NDMP server from the backup infrastructure.

|  |
| --- |
| $ndmp = Get-VBRNDMPServer -Name "NetApp.tech.local"  Remove-VBRNDMPServer -Server $ndmp |

Perform the following steps:

1. Run the [Get-VBRNDMPServer](get-vbrndmpserver.md) cmdlet. Specify the Name parameter values. Save the result to the $ndmp variable.
2. Run the Remove-VBRNDMPServer cmdlet. Set the $ndmp variable as the Server parameter value.

Related Commands

[Get-VBRNDMPServer](get-vbrndmpserver.md)

Page updated 2026-06-04

