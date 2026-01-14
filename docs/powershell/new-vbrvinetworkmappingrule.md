---
title: "New-VBRViNetworkMappingRule"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrvinetworkmappingrule.html"
last_updated: "3/12/2024"
product_version: "13.0.1.1071"
---

# New-VBRViNetworkMappingRule

In this article

Short Description

Defines network mapping rules of isolated networks.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRViNetworkMappingRule -Server <CHost> -ProductionNetwork <VBRViNetworkInfo> -IsolatedNetworkName <string> [-VLANID <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRViVirtualLabNetworkMappingRule object that defines network mapping rules of isolated networks. Veeam Backup & Replication will map isolated networks to production networks that are specified in this rule.

You can use this object to specify network mapping rules in network settings of isolated networks.

Run the [New-VBRViVirtualLabNetworkOptions](new-vbrvivirtuallabnetworkoptions.md) cmdlet to specify network settings of isolated networks.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies an ESXi host. The cmdlet will define a network mapping rule for the virtual lab that is added to this host. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | True |
| ProductionNetwork | Specifies a production network with original VMs. The cmdlet will map VMs from this network to VMs from the isolated network. | Accepts the VBRViNetworkInfo object. To get this object, run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. | True | Named | False |
| IsolatedNetworkName | Specifies a name of an isolated network. The cmdlet will create an isolated network with this name. | String | True | Named | False |
| VLANID | Specifies an ID of an isolated network. The cmdlet will create the isolated network with the specified ID. | Int32 | True | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRViVirtualLabNetworkMappingRule object that defines network mapping rules of isolated networks.

Examples

Defining Isolated Mapping Rules

This example shows how to define network mapping rules of isolated networks. The cmdlet output will show details on the following network settings: ProductionNetwork, IsolatedNetworkName and VLANID.

|  |
| --- |
| $server = Get-VBRServer -Name "srv01.tech.local"  $network = Get-VBRViServerNetworkInfo -Server $server  New-VBRViNetworkMappingRule -Server $server -ProductionNetwork $network[3] -IsolatedNetworkName "Sandbox01 Private VM Network" -VLANID 5  ProductionNetwork                       IsolatedNetworkName                                                  VLANID  -----------------                       -------------------                                                  ------  Veeam.Backup.PowerShell.Infos.VBRViN... Sandbox01 Private VM Network                                              5 |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable.
2. Run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $network variable.
3. Run the New-VBRViNetworkMappingRule cmdlet. Specify the following settings:

* Set the $server variable as the Server parameter value.
* Set the $network[3] variable as the ProductionNetwork parameter value.

The Get-VBRViServerNetworkInfo cmdlet will return an array of production networks. Mind the ordinal number of the necessary production network (An array starts with 0. In our example, it is the fourth production network in the array).

* Specify the IsolatedNetworkName parameter value.
* Specify the VLANID parameter value.

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md)

Page updated 3/12/2024

Page content applies to build 13.0.1.1071
