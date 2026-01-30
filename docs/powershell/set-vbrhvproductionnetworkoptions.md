---
title: "Set-VBRHvProductionNetworkOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrhvproductionnetworkoptions.html"
last_updated: "4/30/2024"
product_version: "13.0.1.1071"
---

# Set-VBRHvProductionNetworkOptions


Short Description

Modifies production network options for Hyper-V virtual lab.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRHvProductionNetworkOptions -ProductionNetworkOptions <VBRHvProductionNetworkOptions> [-ProductionNetwork <VBRHvServerNetworkInfo>] [-UseProductionNetworkVLANID] [-ProductionNetworkVLanID <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies production network options for Hyper-V virtual lab.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ProductionNetworkOptions | Specifies options of a production network. The cmdlet will modify settings of this network. | Accepts the VBRHvProductionNetworkOptions object. To create this object, run the [New-VBRHvProductionNetworkOptions](new-vbrhvproductionnetworkoptions.md) cmdlet. | True | Named | False |
| ProductionNetwork | Specifies a production network with original VMs. The cmdlet will map VMs from this network to VMs from the isolated network. | Accepts the VBRHvServerNetworkInfo object. To get this object, run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. | False | Named | False |
| UseProductionNetworkVLANID | Defines that the cmdlet will enable a production network VLANID. | SwitchParameter | False | Named | False |
| ProductionNetworkVLANID | Specifies an ID of a production network. The cmdlet will create the production network with the specified ID. | Int | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRHvProductionNetworkOptions object that defines options of a production network.

Examples

Modifying Production Network Options

This example shows how to modify production network options.

|  |
| --- |
| $server = Get-VBRServer -Name "srv01.tech.local"  $network = Get-VBRHvServerNetworkInfo -Server $server  $prod = New-VBRHvProductionNetworkOptions -ProductionNetwork $network[3] -UseProductionNetworkVLANID -ProductionNetworkVLANID "2"  Set-VBRHvProductionNetworkOptions -ProductionNetworkOptions $prod -ProductionNetworkVLANID "3" |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $network variable.
3. Run the [New-VBRHvProductionNetworkOptions](new-vbrhvproductionnetworkoptions.md) cmdlet. Specify the ProductionNetwork, UseProductionNetworkVLANID and ProductionNetworkVLANID parameter values. Save the result to the $prod variable.

1. Run the Set-VBRHvProductionNetworkOptions cmdlet. Set the $prod variable as the ProductionNetworkOptions parameter value. Specify the ProductionNetworkVLANID parameter value.

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md)
* [New-VBRHvProductionNetworkOptions](new-vbrhvproductionnetworkoptions.md)


