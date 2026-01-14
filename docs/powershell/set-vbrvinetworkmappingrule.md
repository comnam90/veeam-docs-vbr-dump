---
title: "Set-VBRViNetworkMappingRule"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrvinetworkmappingrule.html"
last_updated: "4/30/2024"
product_version: "13.0.1.1071"
---

# Set-VBRViNetworkMappingRule

In this article

Short Description

Modifies network mapping rules of isolated networks.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRViNetworkMappingRule [-NetworkMapping <VBRViVirtualLabNetworkMappingRule>] [-ProductionNetwork <VBRViNetworkInfo>] [-IsolatedNetworkName <string>] [-VLANID <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies network mapping rules of isolated networks.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| NetworkMapping | Specifies the network mapping rule of isolated networks. The cmdlet will modify settings of this network mapping rule. | Accepts the VBRViVirtualLabNetworkMappingRule object. To create this object, run the [New-VBRViNetworkMappingRule](new-vbrvinetworkmappingrule.md) cmdlet. | True | Named | False |
| ProductionNetwork | Specifies a production network with original VMs. The cmdlet will map VMs from this network to VMs from the isolated network. | Accepts the VBRViNetworkInfo object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | False | Named | False |
| IsolatedNetworkName | Specifies a name of an isolated network. The cmdlet will create an isolated network with this name. | String | False | Named | False |
| VLANID | Specifies an ID of an isolated network. The cmdlet will create the isolated network with the specified ID. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRViVirtualLabNetworkMappingRule object that defines network mapping rules of isolated networks.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Mapping to Production Network

|  |  |
| --- | --- |
| This example shows how to modify mapping rule and to map an isolated network to another production network.  |  | | --- | | $server = Get-VBRServer -Name "srv01.tech.local"  $production = Get-VBRViServerNetworkInfo -Server $server  $isolated = New-VBRViNetworkMappingRule -ProductionNetwork $production[3] -IsolatedNetworkName "Sandbox01 Private VM Network" -VLANID 5  Set-VBRViNetworkMappingRule -NetworkMapping $isolated -ProductionNetwork $production[7] |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $production variable. 3. Run the [New-VBRViNetworkMappingRule](new-vbrvinetworkmappingrule.md) cmdlet. Specify the ProductionNetwork, IsolatedNetworkName and VLANID parameter values. Save the result to the $isolated variable.  1. Run the Set-VBRViNetworkMappingRule cmdlet. Set the $isolated variable as the NetworkMapping parameter value. Set the $production[7] variable as the ProductionNetwork parameter value.   The Get-VBRViServerNetworkInfo cmdlet will return an array of production networks. Mind the ordinal number of the necessary production network (An array starts with 0. In our example, it is the sixth production network in the array). |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Isolated Network Name and ID

|  |  |
| --- | --- |
| This example shows how to modify a name and ID of an isolated network.  |  | | --- | | $server = Get-VBRServer -Name "srv01.tech.local"  $production = Get-VBRViServerNetworkInfo -Server $server  $isolated = New-VBRViNetworkMappingRule -ProductionNetwork $production[3] -IsolatedNetworkName "Sandbox01 Private VM Network" -VLANID 5  Set-VBRViNetworkMappingRule -NetworkMapping $isolated -IsolatedNetworkName "Sandbox07 Private VM Network" -VLANID 7 |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $production variable. 3. Run the [New-VBRViNetworkMappingRule](new-vbrvinetworkmappingrule.md) cmdlet. Specify the ProductionNetwork, IsolatedNetworkName and VLANID parameter values. Save the result to the $isolated variable.  1. Run the Set-VBRViNetworkMappingRule cmdlet. Specify the following settings:  * Set the $isolated variable as the NetworkMapping parameter value. * Specify the IsolatedNetworkName parameter value. * Specify the VLANID parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md)

* [New-VBRViNetworkMappingRule](new-vbrvinetworkmappingrule.md)

Page updated 4/30/2024

Page content applies to build 13.0.1.1071
