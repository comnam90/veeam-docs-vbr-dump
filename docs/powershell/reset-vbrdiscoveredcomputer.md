---
title: "Reset-VBRDiscoveredComputer"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/reset-vbrdiscoveredcomputer.html"
last_updated: "5/3/2024"
product_version: "13.0.1.1071"
---

# Reset-VBRDiscoveredComputer

In this article

Short Description

Reboots discovered computers.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Reset-VBRDiscoveredComputer -DiscoveredComputer <VBRDiscoveredComputer[]> [-RunAsync] [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet reboots selected discovered computers.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| DiscoveredComputer | Specifies the array of discovered computers. The cmdlet will reboot these computers. | Accepts the [VBRDiscoveredComputer](vbrdiscoveredcomputer.md)[[]](vbrdiscoveredcomputer.md) object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if the user is sure that he wants to continue. | SwitchParameter | False | Named | False |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | True (ByPropertyName) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRSession](vbrsession.md)

Examples

Rebooting Discovered Computers of Protection Group

This example shows how to reboot discovered computers of a protection group.

|  |
| --- |
| $group = Get-VBRProtectionGroup -Name "East Support"  $discovered = Get-VBRDiscoveredComputer -ProtectionGroup $group  Reset-VBRDiscoveredComputer -DiscoveredComputer $discovered |

Perform the following steps:

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable.
2. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Set the $group variable as the ProtectionGroup parameter value. Save the result to the $discovered variable.
3. Run the Reset-VBRDiscoveredComputer cmdlet. Set the $discovered variable as the DiscoveredComputer parameter value.

Related Commands

* [Get-VBRProtection](get-vbrprotectiongroup.md)
* [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md)

Page updated 5/3/2024

Page content applies to build 13.0.1.1071
