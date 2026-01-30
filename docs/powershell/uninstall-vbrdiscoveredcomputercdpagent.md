---
title: "Uninstall-VBRDiscoveredComputerCDPAgent"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/uninstall-vbrdiscoveredcomputercdpagent.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Uninstall-VBRDiscoveredComputerCDPAgent


Short Description

Removes Veeam CDP Guest Service and Veeam CDP volume filter driver.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Uninstall-VBRDiscoveredComputerCDPAgent -DiscoveredComputer <VBRDiscoveredComputer[]> [-RunAsync] [-WhatIf] [-Confirm] [<CommonParameters] |

Detailed Description

This cmdlet removes Veeam CDP Guest Service and Veeam CDP volume filter driver from the specified workloads.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| DiscoveredComputer | Specifies workloads in a protection group. The cmdlet will remove the service and driver from these workloads. | Accepts the VBRDiscoveredComputer object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | True | Named | True |
| RunAsync | Defines that the command returns immediately without waiting for the task to complete. | SwitchParameter | False | Named | True |
| WhatIf | Defines that the cmdlet will write a message that describes the effects of running the cmdlet without actually performing any action. | SwitchParameter | False | Named | False |
| Confirm | Defines that the cmdlet will display a prompt that asks if you want to continue running the command. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRSession object that defines options of the removal session.

Examples

Uninstalling CDP Guest Service

This example shows how to remove Veeam CDP Guest Service and Veeam CDP volume filter driver from workloads in the Protection Group CDP protection group.

|  |
| --- |
| $group = Get-VBRProtectionGroup -Name "Protection Group CDP"  $workload = Get-VBRDiscoveredComputer -ProtectionGroup $group  Uninstall-VBRDiscoveredComputerCDPAgent -DiscoveredComputer $workload |

Perform the following steps:

1. Run the [Get-VBRProtectionGroup](get-vbrprotectiongroup.md) cmdlet. Specify the Name parameter value. Save the result to the $group variable.
2. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Set the $group variable as the ProtectionGroup parameter value. Save the result to the $workload variable.
3. Run the Uninstall-VBRDiscoveredComputerCDPAgent cmdlet. Set the $workload variable as the DiscoveredComputer parameter value.

Related Commands

* [Get-VBRProtectionGroup](get-vbrprotectiongroup.md)

* [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md)


