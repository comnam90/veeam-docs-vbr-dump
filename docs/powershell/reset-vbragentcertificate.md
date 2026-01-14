---
title: "Reset-VBRAgentCertificate"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/reset-vbragentcertificate.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Reset-VBRAgentCertificate

In this article

Short Description

Resets Veeam Agents SSL certificates.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Reset-VBRAgentCertificate -DiscoveredComputer <VBRDiscoveredComputer[]> [-WhatIf] [-Confirm]  [<CommonParameters>] |

Detailed Description

This cmdlet resets SSL certificates for selected Veeam Agents.

When you reset Veeam Agents certificates, all backup jobs run by these agents stop. You can use this cmdlet for performing Maintenance tasks on protected computers where the associated agents are installed.

Veeam Backup & Replication will regenerate a new Veeam Agent certificate automatically next time you run a Veeam Agent backup job.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| DiscoveredComputer | Specifies the array of discovered computers. The cmdlet will reset SSL certificates for Veeam Agents installed on these computers.  Note: You can reset the SSL certificate only on discovered computers. | Accepts the [VBRDiscoveredComputer[]](vbrdiscoveredcomputer.md) object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |
| WhatIf | Defines whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines whether the cmdlet displays a prompt that asks if the user is sure that they want to continue. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Resetting SSL Certificates for Veeam Agents on Computers of Selected Protection Group

|  |  |
| --- | --- |
| This example shows how to reset SSL certificates for Veeam Agents installed on computers of a selected protection group.  |  | | --- | | $group = Get-VBRProtectionGroup -Name "East Support"  $discovered = Get-VBRDiscoveredComputer -ProtectionGroup $group  Reset-VBRAgentCertificate -DiscoveredComputer $discovered |  Perform the following steps:   1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 2. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Set the $group variable as the ProtectionGroup parameter value. Save the result to the $discovered variable. 3. Run the Reset-VBRAgentCertificate cmdlet. Set the $discovered variable as the DiscoveredComputer parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Resetting SSL Certificate for Veeam Agent Installed on Selected Computer

|  |  |
| --- | --- |
| This example shows how to reset the SSL certificate for Veeam Agent installed on a selected computer.  |  | | --- | | $group = Get-VBRProtectionGroup -Name "East Support"  $comp = Get-VBRDiscoveredComputer -ProtectionGroup $group | where {$\_.name -eq "support1.east.local"}  Reset-VBRAgentCertificate -DiscoveredComputer $comp |  Perform the following steps:   1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable. 2. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Set the $group variable as the ProtectionGroup parameter value. Use the Where-Object method to get the discovered computer. Save the result to the $comp variable. 3. Run the Reset-VBRAgentCertificate cmdlet. Set the $comp variable as the DiscoveredComputer parameter value. |

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)

* [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md)

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
