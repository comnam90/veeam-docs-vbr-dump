---
title: "Set-VBRHvIsolatedNetworkOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrhvisolatednetworkoptions.html"
last_updated: "4/30/2024"
product_version: "13.0.1.1071"
---

# Set-VBRHvIsolatedNetworkOptions

In this article

Short Description

Modifies network settings of isolated networks for Hyper-V virtual lab.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRHvIsolatedNetworkOptions -IsolatedNetworkOptions <VBRHvIsolatedNetworkOptions> [-ProductionNetworkOptions <VBRHvProductionNetworkOptions[]>] [-IsolatedNetworkName <string>] [-IsolatedNetworkVLANID <int>] [-IPAddress <ipaddress>] [-SubnetMask <string>] [-MasqueradeIPAddress <ipaddress>] [-DNSServer <ipaddress[]>] [-EnableDHCP] [-IPv6Address <ipaddress>] [-IPv6PrefixLength <int>] [-MasqueradeIPv6Address <ipaddress>] [-IPv6DNSServer <ipaddress[]>] [-EnableDHCPv6]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies network settings of isolated Hyper-V networks and how to map it to production networks.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| IsolatedNetworkOptions | Specifies network settings that you want to modify. | Accepts the VBRHvIsolatedNetworkOptions object. To create this object, run the [New-VBRHvIsolatedNetworkOptions](new-vbrhvisolatednetworkoptions.md) cmdlet. | True | Named | True (ByValue, |
| ProductionNetworkOptions | Specifies a network mapping rule of an isolated network. The cmdlet will map the isolated network to the production network that is specified in this rule. | Accepts the VBRHvProductionNetworkOptions[] object. To create this object, run the [New-VBRHvProductionNetworkOptions](new-vbrhvproductionnetworkoptions.md) cmdlet. | False | Named | False |
| IsolatedNetworkName | Specifies a name of an isolated network. The cmdlet will create an isolated network with this name. | String | False | Named | False |
| IsolatedNetworkVLANID | Specifies an ID of a isolated network. The cmdlet will create the isolated network with the specified ID. | Int | False | Named | False |
| IPAddress | Specifies an IP address of the proxy appliance. Veeam Backup & Replication will use this IP address to connect an isolated network with the production network. | IPAddress | False | Named | False |
| IPv6Address | Specifies an IPv6 address of the proxy appliance. Veeam Backup & Replication will use this IP address to connect an isolated network with the production network. | IPAddress | False | Named | False |
| SubnetMask | Specifies a subnet mask of an isolated network. | String | False | Named | False |
| IPv6PrefixLength | Specifies a prefix length of an isolated network. | <int> | False | Named | False |
| MasqueradeIPAddress | Specifies a masquerade IP address. Veeam Backup & Replication will use this IP address to access VMs in the isolated network from the production network. | IPAddress | False | Named | False |
| MasqueradeIPv6Address | Specifies a masquerade IPv6 address. Veeam Backup & Replication will use this IP address to access VMs in the isolated network from the production network. | IPAddress | False | Named | False |
| DNSServer | Specifies an array of IP addresses of virtualized DNS servers. | IPAddress[] | False | Named | False |
| IPv6DNSServer | Specifies an array of IPv6 addresses of virtualized DNS servers. | IPAddress[] | False | Named | False |
| EnableDHCP | Defines that the cmdlet will enable the DHCP service.  If you provide this parameter, Veeam Backup & Replication will dynamically assign IP addresses for isolated VMs. Otherwise, you must assign the IP addresses manually. | SwitchParamter | False | Named | False |
| EnableDHCPv6 | Defines that the cmdlet will enable the DHCPv6 service.  If you provide this parameter, Veeam Backup & Replication will dynamically assign IP addresses for isolated VMs. Otherwise, you must assign the IP addresses manually. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRHvIsolatedNetworkOptions object that defines network settings of isolated networks and how to map it to production networks.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Subnet Mask

|  |  |
| --- | --- |
| This example shows how to modify a subnet mask of an isolated network that connects to the to production network.  |  | | --- | | $server = Get-VBRServer -Name "srv01.tech.local"  $network = Get-VBRHvServerNetworkInfo -Server $server  $prodnet = New-VBRHvProductionNetworkOptions -ProductionNetwork $network[3] -UseProductionNetworkVLANID -ProductionNetworkVLANID "2"  $isolated = New-VBRHvIsolatedNetworkOptions -ProductionNetworkOptions $prodnet -IPAddress 172.17.1.2 -SubnetMask 255.255.0.0 -MasqueradeAddress 172.22.22.22  Set-VBRHvIsolatedNetworkOptions -IsolatedNetworkOptions $isolated -SubnetMask 255.255.255.0 |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $network variable. 3. Run the [New-VBRHvProductionNetworkOptions](new-vbrhvproductionnetworkoptions.md) cmdlet. Specify the ProductionNetwork and ProductionNetworkVLANID parameter values. Provide the UseProductionNetworkVLANID parameter. Save the result to the $prodnet variable. 4. Run the [New-VBRHvIsolatedNetworkOptions](new-vbrhvisolatednetworkoptions.md) cmdlet. Specify the ProductionNetworkOptions, IPAddress, SubnetMask and MasqueradeAddress parameter values. Save the result to the $isolated variable. 5. Run the Set-VBRHvIsolatedNetworkOptions cmdlet. Set the $isolated variable as the IsolatedNetworkOptions parameter value. Specify the SubnetMask parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Prefix Length

|  |  |
| --- | --- |
| This example shows how to modify a prefix length of an isolated network that connects to the to production network.  |  | | --- | | $server = Get-VBRServer -Name "srv01.tech.local"  $network = Get-VBRHvServerNetworkInfo -Server $server  $prodnet = New-VBRHvProductionNetworkOptions -ProductionNetwork $network[3] -UseProductionNetworkVLANID -ProductionNetworkVLANID "2"  $isolated = New-VBRHvIsolatedNetworkOptions -ProductionNetworkOptions $prodnet -IPv6Address fdd1:aa80:bb80:cc80:dd80:ee80:fe80:10 -IPv6PrefixLength 64 -MasqueradeIPv6Address fdd1:ab80:bb80:cc88::  Set-VBRHvIsolatedNetworkOptions -IsolatedNetworkOptions $isolated -IPv6PrefixLength 32 |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $network variable. 3. Run the [New-VBRHvProductionNetworkOptions](new-vbrhvproductionnetworkoptions.md) cmdlet. Specify the ProductionNetwork and ProductionNetworkVLANID parameter values. Provide the UseProductionNetworkVLANID parameter. Save the result to the $prodnet variable. 4. Run the [New-VBRHvIsolatedNetworkOptions](new-vbrhvisolatednetworkoptions.md) cmdlet. Specify the ProductionNetworkOptions, IPv6Address, IPv6PrefixLength and MasqueradeIPv6Address parameter values. Save the result to the $isolated variable. 5. Run the Set-VBRHvIsolatedNetworkOptions cmdlet. Set the $isolated variable as the IsolatedNetworkOptions parameter value. Specify the IPv6PrefixLength parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md)
* [New-VBRHvProductionNetworkOptions](new-vbrhvproductionnetworkoptions.md)
* [New-VBRHvIsolatedNetworkOptions](new-vbrhvisolatednetworkoptions.md)

Page updated 4/30/2024

Page content applies to build 13.0.1.1071
