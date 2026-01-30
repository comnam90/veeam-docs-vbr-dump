---
title: "New-VBRUniversalCDPNetworkMappingRule"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbruniversalcdpnetworkmappingrule.html"
last_updated: "11/20/2025"
product_version: "13.0.1.1071"
---

# New-VBRUniversalCDPNetworkMappingRule


Short Description

Defines network mapping rules for universal CDP policies.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Define the default target network used for workloads and network adapters for which mapping rules are not defined explicitly.

|  |
| --- |
| New-VBRUniversalCDPNetworkMappingRule -IsDefaultNetwork -TargetNetwork <IVBRServerNetworkInfo> [<CommonParameters>] |

* Define a network mapping rule for a workload or network adapter.

|  |
| --- |
| New-VBRUniversalCDPNetworkMappingRule -SourceObject <VBRUniversalCDPSourceNetwork> -TargetNetwork <IVBRServerNetworkInfo> [<CommonParameters>] |

Detailed Description

This cmdlet defines the VBRUniversalCDPNetworkMappingRule object that contains network mapping rules.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| IsDefaultNetwork | Defines that the cmdlet specifies the default target network. If you provide this parameter, the target network will be used for all workloads and network adapters for which mapping rules are not defined explicitly. | SwitchParameter | True | Named | False |
| TargetNetwork | Specifies the target network. | Accepts the IVBRServerNetworkInfo object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | True | Named | False |
| SourceObject | Specifies the workload or network adapter for which you want to create the rule. | Accepts the VBRUniversalCDPSourceNetwork object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) or [Get-VBRDiscoveredComputerNetwork](get-vbrdiscoveredcomputernetwork.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRUniversalCDPNetworkMappingRule object that defines network mapping rules.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating Network Rule for Workload

|  |  |
| --- | --- |
| This example shows how to create a network mapping rule for a workload.  |  | | --- | | $workloads = Get-VBRDiscoveredComputer  $server = Get-VBRServer -Name "prgtwesx01-virt.tech.local"  $networks = Get-VBRViServerNetworkInfo -Server $server  $rule = New-VBRUniversalCDPNetworkMappingRule -SourceObject $workloads[0] -TargetNetwork $networks[0] |  Perform the following steps:   1. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Save the result to the $workloads variable. 2. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 3. Run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $networks variable. 4. Run the New-VBRUniversalCDPNetworkMappingRule cmdlet. Set the $workloads[0] variable as the SourceObject parameter value. Set the $networks[0] variable as the TargetNetwork parameter value. Save the result to the $rule variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Default Network Rule

|  |  |
| --- | --- |
| This example shows how to create the default network rule.  |  | | --- | | $server = Get-VBRServer -Name "prgtwesx01-virt.tech.local"  $networks = Get-VBRViServerNetworkInfo -Server $server  $rule = New-VBRUniversalCDPNetworkMappingRule -IsDefaultNetwork -TargetNetwork $networks[0] |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $networks variable. 3. Run the New-VBRUniversalCDPNetworkMappingRule cmdlet. Provide the IsDefaultNetwork parameter. Set the $networks[0] variable as the TargetNetwork parameter value. Save the result to the $rule variable. |

Related Commands

* [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md)
* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md)


