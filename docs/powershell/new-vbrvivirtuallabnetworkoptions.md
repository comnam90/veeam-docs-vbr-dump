---
title: "New-VBRViVirtualLabNetworkOptions"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrvivirtuallabnetworkoptions.html"
last_updated: "4/30/2024"
product_version: "13.0.1.1071"
---

# New-VBRViVirtualLabNetworkOptions


Short Description

Defines network settings of isolated networks.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRViVirtualLabNetworkOptions -NetworkMappingRule <VBRViVirtualLabNetworkMappingRule> [-IPAddress <ipaddress>] [-SubnetMask <string>] [-MasqueradeIPAddress <ipaddress>] [-DNSServer <ipaddress[]>] [-EnableDHCP] [-IPv6Address <ipaddress>] [-IPv6PrefixLength <int>] [-MasqueradeIPv6Address <ipaddress>] [-IPv6DNSServer <ipaddress[]>] [-EnableDHCPv6]  [<CommonParameters>] |

Detailed Description

This cmdlet creates the VBRViVirtualLabNetworkOption object that defines network settings of isolated networks and how to map it to production networks.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| NetworkMappingRule | Specifies a network mapping rule of an isolated network. The cmdlet will map the isolated network to the production network that is specified in this rule. | Accepts the VBRViVirtualLabNetworkMappingRule object. To create this object, run the[New-VBRViNetworkMappingRule](new-vbrvinetworkmappingrule.md) cmdlet. | True | Named | True (ByValue, |
| IPAddress | Specifies an IPv4 address of the proxy appliance. Veeam Backup & Replication will use this IP address to connect an isolated network with the production network. | IPAddress | False | Named | False |
| IPv6Address | Specifies an IPv6 address of the proxy appliance. Veeam Backup & Replication will use this IP address to connect an isolated network with the production network. | IPAddress | False | Named | False |
| SubnetMask | Specifies a subnet mask of an isolated network. | String | False | Named | False |
| IPv6PrefixLength | Specifies a prefix length of an isolated network. | <int> | False | Named | False |
| MasqueradeIPAddress | Specifies a masquerade IPv4 address. Veeam Backup & Replication will use this IP address to access VMs in the isolated network from the production network. | IPAddress | False | Named | False |
| MasqueradeIPv6Address | Specifies a masquerade IPv6 address. Veeam Backup & Replication will use this IP address to access VMs in the isolated network from the production network. | IPAddress | False | Named | False |
| DNSServer | Specifies an array of IPv4 addresses of virtualized DNS servers. | IPAddress[] | False | Named | False |
| IPv6DNSServer | Specifies an array of IPv6 addresses of virtualized DNS servers. | IPAddress[] | False | Named | False |
| EnableDHCP | Defines that the cmdlet will enable the DHCP service.  If you provide this parameter, Veeam Backup & Replication will dynamically assign IP addresses for isolated VMs. Otherwise, you must assign the IP addresses manually. | SwitchParamter | False | Named | False |
| EnableDHCPv6 | Defines that the cmdlet will enable the DHCPv6 service.  If you provide this parameter, Veeam Backup & Replication will dynamically assign IP addresses for isolated VMs. Otherwise, you must assign the IP addresses manually. | SwitchParamter | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRViVirtualLabNetworkOption object that defines network settings of isolated networks and how to map it to production networks.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Network Settings of Isolated Network Using IPv4

|  |  |
| --- | --- |
| This example shows how to define network settings of the Sandbox01 Private VM Network isolated network to map to the production network using IPv4. The isolated network will be set up with the following settings:   * The IP address of the proxy appliance is assigned the 172.17.1.2 IP. * The subnet mask is set to 255.255.0.0. * The masquerade IP address is set to 172.22.22.22.     |  | | --- | | $server = Get-VBRServer -Name "srv01.tech.local"  $network = Get-VBRViServerNetworkInfo -Server $server  $maprule = New-VBRViNetworkMappingRule -ProductionNetwork $network[3] -IsolatedNetworkName "Sandbox01 Private VM Network" -VLANID 5  New-VBRViVirtualLabNetworkOptions -NetworkMappingRule $maprule -IPAddress 172.17.1.2 -SubnetMask 255.255.0.0 -MasqueradeAddress 172.22.22.22 |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $network variable. 3. Run the [New-VBRViNetworkMappingRule](new-vbrvinetworkmappingrule.md) cmdlet. Specify the ProductionNetwork, IsolatedNetworkName and VLANID parameters. Save the result to the $maprule variable. 4. Run the New-VBRViVirtualLabNetworkOptions cmdlet. Specify the following settings:  * Set the $maprule variable as the NetworkMappingRule parameter value. * Specify the IPAddress parameter value. * Specify the SubnetMask parameter value. * Specify the MasqueradeIPAddress parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Network Settings of Isolated Network Using IPv6

|  |  |
| --- | --- |
| This example shows how to define network settings of the Sandbox01 Private VM Network isolated network to map to the production network using IPv6. The isolated network will be set up with the following settings:   * The IP address of the proxy appliance is assigned the fdd1:aa80:bb80:cc80:dd80:ee80:fe80:10 IP. * The prefix length is set to 64. * The masquerade IP address is set to fdd1:ab80:bb80:cc88::.     |  | | --- | | $server = Get-VBRServer -Name "srv01.tech.local"  $network = Get-VBRViServerNetworkInfo -Server $server  $maprule = New-VBRViNetworkMappingRule -ProductionNetwork $network[3] -IsolatedNetworkName "Sandbox01 Private VM Network" -VLANID 5  New-VBRViVirtualLabNetworkOptions -NetworkMappingRule $maprule -IPv6Address fdd1:aa80:bb80:cc80:dd80:ee80:fe80:10 -IPv6PrefixLength 64 -MasqueradeIPv6Address fdd1:ab80:bb80:cc88:: |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $network variable. 3. Run the New-VBRViNetworkMappingRule cmdlet. Specify the ProductionNetwork, IsolatedNetworkName and VLANID parameters. Save the result to the $maprule variable. 4. Run the New-VBRViVirtualLabNetworkOptions cmdlet. Specify the following settings:  * Set the $maprule variable as the NetworkMappingRule parameter value. * Specify the IPv6Address parameter value. * Specify the IPv6PrefixLength parameter value. * Specify the MasqueradeIv6PAddress parameter value. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 3. Defining Network Settings of Isolated Network with DHCP Service and DNS Server Using IPv4

|  |  |
| --- | --- |
| This example shows how to define network settings of the Sandbox01 Private VM Network isolated network to connect to map to the production network using the DHCP Service and DNS Server and IPv4.  |  | | --- | | $server = Get-VBRServer -Name "srv01.tech.local"  $network = Get-VBRViServerNetworkInfo -Server $server  $maprule = New-VBRViNetworkMappingRule -ProductionNetwork $network[3] -IsolatedNetworkName "Sandbox01 Private VM Network" -VLANID 5  New-VBRViVirtualLabNetworkOptions -NetworkMappingRule $maprule -IPAddress 172.17.1.2 -SubnetMask 255.255.0.0 -MasqueradeIPAddress 172.22.22.22 -DNSServer 192.168.1.99 -EnableDHCP |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $network variable. 3. Run the [New-VBRViNetworkMappingRule](new-vbrvinetworkmappingrule.md) cmdlet. Specify the ProductionNetwork, IsolatedNetworkName and VLANID parameters. Save the result to the $maprule variable. 4. Run the New-VBRViVirtualLabNetworkOptions cmdlet. Specify the following settings:  * Set the $maprule variable as the NetworkMappingRule parameter value. * Specify the IPAddress parameter value. * Specify the SubnetMask parameter value. * Specify the MasqueradeIPAddress parameter value. * Specify the DNSServer parameter value. * Provide the EnableDHCP parameter. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 4. Defining Network Settings of Isolated Network with DHCP Service and DNS Server Using IPv6

|  |  |
| --- | --- |
| This example shows how to define network settings of the Sandbox01 Private VM Network isolated network to connect to map to the production network using the DHCP Service and DNS Server and IPv6.  |  | | --- | | $server = Get-VBRServer -Name "srv01.tech.local"  $network = Get-VBRViServerNetworkInfo -Server $server  $maprule = New-VBRViNetworkMappingRule -ProductionNetwork $network[3] -IsolatedNetworkName "Sandbox01 Private VM Network" -VLANID 5  New-VBRViVirtualLabNetworkOptions -NetworkMappingRule $maprule -IPv6Address fdd1:aa80:bb80:cc80:dd80:ee80:fe80:10 -IPv6PrefixLength 64 -MasqueradeIPv6Address fdd1:ab80:bb80:cc88:: -IPv6DNSServer fdd1:aa80:bb80:cc80:dd80:ee80:ff80:3 -EnableDHCPv6 |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $server variable. 2. Run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value. Save the result to the $network variable. 3. Run the [New-VBRViNetworkMappingRule](new-vbrvinetworkmappingrule.md) cmdlet. Specify the ProductionNetwork, IsolatedNetworkName and VLANID parameters. Save the result to the $maprule variable. 4. Run the New-VBRViVirtualLabNetworkOptions cmdlet. Specify the following settings:  * Set the $maprule variable as the NetworkMappingRule parameter value.  * Specify the IPv6Address parameter value. * Specify the IPv6PrefixLength parameter value. * Specify the MasqueradeIv6PAddress parameter value.  * Specify the IPv6DNSServer parameter value. * Provide the EnableDHCPv6 parameter. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md)
* [New-VBRViNetworkMappingRule](new-vbrvinetworkmappingrule.md)


