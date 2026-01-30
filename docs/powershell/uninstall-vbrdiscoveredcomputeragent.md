---
title: "Uninstall-VBRDiscoveredComputerAgent"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/uninstall-vbrdiscoveredcomputeragent.html"
last_updated: "5/7/2024"
product_version: "13.0.1.1071"
---

# Uninstall-VBRDiscoveredComputerAgent


Short Description

Removes Veeam Agent from a specific protected computer.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Uninstall-VBRDiscoveredComputerAgent -DiscoveredComputer <VBRDiscoveredComputer[]> [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet removes Veeam Agent from a specific protected computer.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| DiscoveredComputer | Specifies an array of computers. The cmdlet will remove Veeam Agent from these computers. | Accepts the [VBRDiscoveredComputer](vbrdiscoveredcomputer.md)[] object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | True | Named | True (ByValue, ByPropertyName) |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | True (ByPropertyName) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if the user is sure that he wants to continue.  Note: Microsoft PowerShell enables the Confirm parameter for this cmdlet by default. To disable this option, set the parameter value to $false. That is, Confirm:$false. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

Removing Veeam Agent from Protected Computers

This example shows how to remove Veeam Agent from protected computers that are added to the Support\_East protection group.

|  |
| --- |
| $group = Get-VBRProtectionGroup -Name "Support\_East"  $computers = Get-VBRDiscoveredComputer -ProtectionGroup $group  Uninstall-VBRDiscoveredComputerAgent -DiscoveredComputer $computers |

Perform the following steps:

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable.
2. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Set the $group variable as the ProtectionGroup parameter value. Save the result to the $computers variable.
3. Run the Uninstall-VBRDiscoveredComputerAgent cmdlet. Set the $computers variable as the DiscoveredComputer parameter value.

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)
* [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md)


