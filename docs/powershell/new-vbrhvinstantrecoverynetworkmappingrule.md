---
title: "New-VBRHvInstantRecoveryNetworkMappingRule"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrhvinstantrecoverynetworkmappingrule.html"
last_updated: "4/4/2024"
product_version: "13.0.1.1071"
---

# New-VBRHvInstantRecoveryNetworkMappingRule

In this article

Short Description

Creates a new network mapping rule.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRHvInstantRecoveryNetworkMappingRule -SourceNetwork <VBRComputerNetworkInfo> -TargetNetwork <VBRHvServerNetworkInfo>  [<CommonParameters>] |

Detailed Description

This cmdlet defines the VBRHvInstantRecoveryNetworkMappingRule object. This object defines how to map networks in the original site to networks in the target site (site where VMs will be recovered). You can use this object to perform instant recovery of Veeam Agent computers.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| SourceNetwork | Specifies the array of networks connected to Veeam Agent computers. | Accepts the VBRComputerNetworkInfo[] object. To get this object, run the [Get-VBRComputerNetworkInfo](get-vbrcomputernetworkinfo.md) cmdlet. | True | Named | False |
| TargetNetwork | Specifies the array of virtual networks connected to the Hyper-V host which computers are restored to. | Accepts the VBRHvServerNetworkInfo[] object. To get this object, run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRHvInstantRecoveryNetworkMappingRule object that defines network mapping rules.

Examples

Configure network for an appliance

This example shows how to define settings for a new network mapping rule.

|  |
| --- |
| $network = Get-VBRComputerNetworkInfo  New-VBRHvInstantRecoveryNetworkMappingRule -SourceNetwork $network |

Perform the following steps:

1. Run the [Get-VBRComputerNetworkInfo](get-vbrcomputernetworkinfo.md) cmdlet. Save the result to the $network variable.
2. Run the New-VBRHvInstantRecoveryNetworkMappingRule cmdlet. Set the $network variable as the SourceNetwork parameter value.

Page updated 4/4/2024

Page content applies to build 13.0.1.1071
