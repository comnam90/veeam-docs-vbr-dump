---
title: "Uninstall-VBRDiscoveredComputerComponents"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/uninstall-vbrdiscoveredcomputercomponents.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# Uninstall-VBRDiscoveredComputerComponents


Short Description

Uninstalls Veeam components from discovered computers.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Uninstall-VBRDiscoveredComputerComponents -DiscoveredComputer <VBRDiscoveredComputer[]> [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet uninstalls Veeam components, including Veeam Agent, from the specified discovered computers.

Parameters

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| DiscoveredComputer | Specifies the discovered computers from which you want to uninstall Veeam components. | Accepts the array of [VBRDiscoveredComputer](vbrdiscoveredcomputer.md) objects. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| RunAsync | Defines that the cmdlet will run asynchronously. | SwitchParameter | False | Named | True (ByProperty Name) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSession object that contains the uninstall session.

Examples

Uninstalling Veeam Components from Discovered Computers

This example shows how to uninstall Veeam components from discovered computers.

|  |
| --- |
| $computers = Get-VBRDiscoveredComputer  Uninstall-VBRDiscoveredComputerComponents -DiscoveredComputer $computers |

Perform the following steps:

1. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Save the result to the $computers variable.
2. Run the Uninstall-VBRDiscoveredComputerComponents cmdlet. Set the $computers variable as the DiscoveredComputer parameter value.

Related Commands

[Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md)

Page updated 2026-06-04

