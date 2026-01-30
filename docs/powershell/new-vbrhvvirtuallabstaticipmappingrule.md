---
title: "New-VBRHvVirtualLabStaticIPMappingRule"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrhvvirtuallabstaticipmappingrule.html"
last_updated: "5/2/2024"
product_version: "13.0.1.1071"
---

# New-VBRHvVirtualLabStaticIPMappingRule


Short Description

Defines static IP address mapping rules.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRHvVirtualLabIPMappingRule -ProductionNetwork <VBRHvServerNetworkInfo> [-IsolatedIPAddress <ipaddress>] [-AccessIPAddress <ipaddress>] [-IsolatedIPv6Address <ipaddress>] [-AccessIPv6Address <ipaddress>] [-Note <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRHvVirtualLabStaticIPMappingRule object that defines static IP address mapping rules.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ProductionNetwork | Specifies a production network with original VMs. The cmdlet will set up static mapping of IP address from this network with IP addresses from the isolated network. | Accepts the VBRHvServerNetworkInfo object. To get this object, run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. | True | Named | False |
| IsolatedIPAddress | Specifies an IPv4 address of an isolated network. The cmdlet will map this IP address with an IP address of a production network. | IPAddress | False | Named | False |
| AccessIPAddress | Specifies an IPv4 address of a production network. The cmdlet will map this IP address with an IP address of an isolated network. | IPAddress | False | Named | False |
| IsolatedIPv6Address | Specifies an IPv6 address of an isolated network. The cmdlet will map this IP address with an IP address of a production network. | IPAddress | False | Named | False |
| AccessIPv6Address | Specifies an IPv6 address of a production network. The cmdlet will map this IP address with an IP address of an isolated network. | IPAddress | False | Named | False |
| Note | Specifies notes that you want to assign to the static mapping settings. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRHvVirtualLabStaticIPMappingRule object that defines static IP address mapping rules.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Static IPv4 Address Mapping Rules

|  |  |
| --- | --- |
| This example shows how to define static IPv4 address mapping rules. The cmdlet output will contain the following details on mapping settings: ProductionNetwork, IsolatedIPAddress, AccessIPAddress and Note.  |  | | --- | | $server = Get-VBRServer -Name "srv01.tech.local"  $network = Get-VBRHvServerNetworkInfo -Server $server  New-VBRHvVirtualLabStaticIPMappingRule -ProductionNetwork $network[2] -IsolatedIPAddress 172.17.53.15 -AccessIPAddress 172.17.53.162 -Note "IP address to access DNS" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $network variable. 3. Run the New-VBRHvVirtualLabStaticIPMappingRule cmdlet. Specify the following settings:  * Set the $network[2] variable as the ProductionNetwork parameter value.   The Get-VBRHvServerNetworkInfo cmdlet will return an array of production networks. Mind the ordinal number of the necessary production network (An array starts with 0. In our example, it is the third production network in the array).   * Specify the IsolatedIPAddress parameter value. * Specify the AccessIPAddress parameter value. * Specify the Note parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Static IPv6 Address Mapping Rules

|  |  |
| --- | --- |
| This example shows how to define static IPv6 address mapping rules. The cmdlet output will contain the following details on mapping settings: ProductionNetwork, IsolatedIPAddress, AccessIPAddress and Note.  |  | | --- | | $server = Get-VBRServer -Name "srv01.tech.local"  $network = Get-VBRViServerNetworkInfo -Server $server  New-VBRHvVirtualLabStaticIPMappingRule -ProductionNetwork $network[2] -IsolatedIPv6Address fdd1:aa80:bb80:cc80:dd80:ee80:ff80:1 -AccessIPv6Address fdd1:aa80:bb80:ac80:dd80:ee80:ff80:1 -Note "IP address to access DNS" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $network variable. 3. Run the New-VBRHvVirtualLabStaticIPMappingRule cmdlet. Specify the following settings:  * Set the $network[2] variable as the ProductionNetwork parameter value.   The Get-VBRHvServerNetworkInfo cmdlet will return an array of production networks. Mind the ordinal number of the necessary production network (An array starts with 0. In our example, it is the third production network in the array).   * Specify the IsolatedIPv6Address parameter value. * Specify the AccessIPv6Address parameter value. * Specify the Note parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Defining Static IPv4 and IPv6 Address Mapping Rules

|  |  |
| --- | --- |
| This example shows how to define static IPv4 and IPv6 address mapping rules. The cmdlet output will contain the following details on mapping settings: ProductionNetwork, IsolatedIPAddress, AccessIPAddress and Note.  |  | | --- | | $server = Get-VBRServer -Name "srv01.tech.local"  $network = Get-VBRHvServerNetworkInfo -Server $server  New-VBRHvVirtualLabStaticIPMappingRule -ProductionNetwork $network[2] -IsolatedIPAddress 192.168.10.20 -AccessIPAddress 192.158.10.20 -IsolatedIPv6Address fdd1:aa80:bb80:cc80:dd80:ee80:ff80:1 -AccessIPv6Address fdd1:aa80:bb80:ac80:dd80:ee80:ff80:1 -Note "IP address to access DNS" |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $network variable. 3. Run the New-VBRHvVirtualLabStaticIPMappingRule cmdlet. Specify the following settings:  * Set the $network[2] variable as the ProductionNetwork parameter value.   The Get-VBRHvServerNetworkInfo cmdlet will return an array of production networks. Mind the ordinal number of the necessary production network (An array starts with 0. In our example, it is the third production network in the array).   * Specify the IsolatedIPAddress parameter value. * Specify the AccessIPAddress parameter value. * Specify the IsolatedIP6Address parameter value. * Specify the AccessIPv6Address parameter value. * Specify the Note parameter value. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md)


