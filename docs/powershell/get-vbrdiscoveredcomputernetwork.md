---
title: "Get-VBRDiscoveredComputerNetwork"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/get-vbrdiscoveredcomputernetwork.html"
last_updated: "11/14/2025"
product_version: "13.0.1.1071"
---

# Get-VBRDiscoveredComputerNetwork


Short Description

Returns network adapters of discovered computers with the Veeam CDP Agent Service installed.

Applies to

Product Edition: Community, Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Get-VBRDiscoveredComputerNetwork -Computer <VBRDiscoveredComputer>  [<CommonParameters>] |

Detailed Description

This cmdlet returns the VBRDiscoveredComputerNetwork object which contains network adapters of the discovered computer. The discovered computer must be added to a protection group and have the Veeam CDP Agent Service installed.

The VBRDiscoveredComputerNetwork object can be used to configure the network mapping rules in a universal CDP policy.

Parameters

| Parameter | Description | Type | Required | Position | Accept |
| --- | --- | --- | --- | --- | --- |
| Computer | Specifies the discovered computer added to a protection group and with the Veeam CDP Agent Service installed. The cmdlet will return the network adapter of this discovered computer. | Accepts the VBRDiscoveredComputer object. To get this object, run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. | True | Named | True (ByValue, ByProperty Name) |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRDiscoveredComputerNetwork[] object that contains network adapters of the discovered computer.

Examples

Getting Network Adapter of Discovered Computer

This example shows how to get the network adapter of a discovered computer.

|  |
| --- |
| $computer = Get-VBRDiscoveredComputer | Where-Object { $\_.Name -eq "serv01" }  $adapters = Get-VBRDiscoveredComputerNetwork -Computer $computer  $netAdapter = $adapters[0] |

Perform the following steps:

1. Run the [Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md) cmdlet. Pipe the cmdlet output to the Where-Object cmdlet. Specify the following settings:

* Provide the $\_. automatic variable.
* Provide the Name property.
* Specify the eq comparison operator value.
* Save the result to the $computer variable.

1. Run the Get-VBRDiscoveredComputerNetwork cmdlet. Set the $computer variable as the Computer parameter value. Save the result to the $adapters variable.

The Get-VBRDiscoveredComputerNetwork cmdlet will return an array of network adapters. Mind the ordinal number of the necessary network adapter. Note that to count objects of the array you must start with 0.

1. Save the $adapters[0] variable to the $netAdapter variable to be used with other cmdlets.

Related Commands

[Get-VBRDiscoveredComputer](get-vbrdiscoveredcomputer.md)


