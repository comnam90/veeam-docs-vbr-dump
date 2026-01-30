---
title: "New-VBRHvProductionNetworkOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrhvproductionnetworkoptions.html"
last_updated: "4/30/2024"
product_version: "13.0.1.1071"
---

# New-VBRHvProductionNetworkOptions


Short Description

Defines production networks options for Hyper-V virtual lab.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRHvProductionNetworkOptions -ProductionNetwork <VBRHvServerNetworkInfo> [-ProductionNetworkVLANID <int>] [-UseProductionNetworkVLANID]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRHvProductionNetworkOptions object that defines network options for Hyper-V production networks.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ProductionNetwork | Specifies a production network with original VMs. | Accepts the VBRHvServerNetworkInfo object. To get this object, run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. | True | Named | False |
| ProductionNetworkVLANID | Specifies an ID of a production network. The cmdlet will create the production network with the specified ID. | Int | False | Named | False |
| UseProductionNetworkVLANID | Defines that the cmdlet will enable a production network VLANID. | SwitchParameter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRHvProductionNetworkOptions object that defines network mapping rules of isolated networks.

Examples

Defining production networks options

This example shows how to define network mapping rules of isolated networks.

|  |
| --- |
| $server = Get-VBRServer -Name "srv01.tech.local"  $network = Get-VBRHvServerNetworkInfo -Server $server  New-VBRHvProductionNetworkOptions -ProductionNetwork $network[3] -UseProductionNetworkVLANID -ProductionNetworkVLANID "2" |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $network variable.
3. Run the New-VBRHvProductionNetworkOptions cmdlet. Specify the following settings:

* Set the $network[3] variable as the ProductionNetwork parameter value.

The Get-VBRHvServerNetworkInfo cmdlet will return an array of production networks. Mind the ordinal number of the necessary production network (An array starts with 0. In our example, it is the fourth production network in the array).

* Provide the UseProductionNetworkVLANID parameter.
* Specify the ProductionNetworkVLANID parameter value.

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md)


