---
title: "New-VBRHvVirtualLabProxyAppliance"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrhvvirtuallabproxyappliance.html"
last_updated: "5/2/2024"
product_version: "13.0.1.1071"
---

# New-VBRHvVirtualLabProxyAppliance


Short Description

Defines settings of proxy appliances.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRHvVirtualLabProxyAppliance -Server <CHost> [-Name <string>] [-Network <VBRHvServerNetworkInfo>] [-VLANID <int>] [-EnableIPv4Interface] [-ObtainIPAutomatically] [-IPAddress <ipaddress>] [-SubnetMask <string>] [-DefaultGateway <ipaddress>] [-ObtainDNSAutomatically] [-PreferredDNSServer <ipaddress>] [-AlternateDNSServer <ipaddress>] [-EnableIPv6Interface] [-ObtainIPv6AddressAutomatically] [-IPv6Address <ipaddress>] [-IPv6PrefixLength <int>] [-IPv6DefaultGateway <ipaddress>] [-ObtainIPv6DNSAutomatically] [-IPv6PreferredDNSServer <ipaddress>] [-IPv6AlternateDNSServer <ipaddress>] [-HTTPPort <int>] [-ProductionProxyIPAddress <ipaddress>] [-EnableInternetProxy]  [<CommonParameters>] |

Detailed Description

This cmdlet defines settings of proxy appliances.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | Specifies a Microsoft Hyper-V host. The cmdlet will deploy a proxy appliance on this host.  Note: The Microsoft Hyper-V host must be the same as the Microsoft Hyper-V host where the virtual lab is created.  This parameter must be the same as the Server parameter in the objects that are created by the following cmdlets:   * [Add-VBRHvAdvancedVirtualLab](add-vbrhvadvancedvirtuallab.md) * [Add-VBRHvSimpleVirtualLab](add-vbrhvsimplevirtuallab.md) * [Set-VBRHvVirtualLab](set-vbrhvvirtuallab.md) | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| Name | Specifies a name of a proxy appliance. The cmdlet will deploy the proxy appliance with this name. | String | False | Named | False |
| Network | Specifies the production network. The cmdlet will connect a proxy appliance to the specified network. | Accepts the VBRHvNetworkInfo object. To get this object, run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. | False | Named | False |
| EnableIPv4Interface | Defines that IPv4 interface will be enabled. | SwitchParameter | False | Named | False |
| ObtainIPAutomatically | Defines that a proxy appliance will obtain an IPv4 address automatically.  If you provide this parameter, Veeam Backup & Replication will obtain an IP address for the proxy appliance automatically. Otherwise, you will need to set the IP address manually. | SwitchParameter | False | Named | False |
| IPAddress | Specifies an IPv4 address for a proxy appliance in the production network. The cmdlet will assign this IP address to a proxy appliance. | IPAddress | False | Named | False |
| SubnetMask | Specifies a subnet mask for a proxy appliance in the production network. The cmdlet will set up network settings of a proxy appliance with this subnet mask. | String | False | Named | False |
| DefaultGateway | Specifies an IPv4 address of a default gateway. The cmdlet will assign this IP address to a default gateway on a proxy appliance. | IPAddress | False | Named | False |
| ObtainDNSAutomatically | Defines that a proxy appliance will obtain DNS server settings automatically.  If you provide this parameter, Veeam Backup & Replication will obtain IPv4 DNS server settings for the proxy appliance automatically. Otherwise, you will need to set the DNS server settings manually. | SwitchParameter | False | Named | False |
| PreferredDNSServer | Specifies an IPv4 address of a preferred DNS server. | IPAddress | False | Named | False |
| AlternateDNSServer | Specifies an IPv4 address of an alternate DNS server. | IPAddress | False | Named | False |
| EnableIPv6Interface | Defines that IPv6 interface will be enabled. | SwitchParameter | False | Named | False |
| ObtainIPv6AddressAutomatically | Defines that a proxy appliance will obtain an IPv6 address automatically.  If you provide this parameter, Veeam Backup & Replication will obtain an IP address for the proxy appliance automatically. Otherwise, you will need to set the IP address manually. | SwitchParameter | False | Named | False |
| IPv6PreferredDNSServer | Specifies an IPv6 address of a preferred DNS server. | IPAddress | False | Named | False |
| IPv6AlternateDNSServer | Specifies an IPv6 address of an alternate DNS server. | IPAddress | False | Named | False |
| IPv6Address | Specifies an IPv6 address for a proxy appliance in the production network. The cmdlet will assign this IP address to a proxy appliance. | IPAddress | False | Named | False |
| IPv6DefaultGateway | Specifies an IPv6 address of a default gateway. The cmdlet will assign this IP address to a default gateway on a proxy appliance. | IPAddress | False | Named | False |
| IPv6PrefixLength | Specifies a prefix length for a proxy appliance in the production network. The cmdlet will set up network settings of a proxy appliance with this prefix length. | String | False | Named | False |
| ObtainIPv6DNSAutomatically | Defines that a proxy appliance will obtain IPv6 DNS server settings automatically.  If you provide this parameter, Veeam Backup & Replication will obtain DNS server settings for the proxy appliance automatically. Otherwise, you will need to set the DNS server settings manually. | SwitchParameter | False | Named | False |
| ProductionProxyIPAddress | Specifies an IP address or a fully qualified domain name of an Internet-facing proxy server that VMs from the isolated network must use to access the Internet. | IPAddress | False | Named | False |
| HTTPPort | Specifies the port number. VMs from the isolated network will use this port number to access the Internet.  Default: 8080. | Int32 | False | Named | False |
| EnableInternetProxy | Defines that a proxy appliance will act as an internet proxy for VMs in the isolated network.  If you provide this parameter, a proxy appliance will act as an internet proxy for VMs in the isolated network. Otherwise, VMs from the isolated network will not have access to the Internet. | SwitchParameter | False | Named | False |
| VLANID | Specifies an ID of an isolated network. The cmdlet will create the isolated network with the specified ID. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRHvVirtualLabProxyAppliance object that defines settings of proxy appliances that are added to the virtual lab.

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Defining Settings of Proxy Appliance with Automatic IP and DNS Setup

|  |  |
| --- | --- |
| This example shows how to define settings of the Proxy\_appliance\_05 proxy appliance that is deployed with the automatic IP and DNS setup. The proxy appliance will be connected to the esx09.tech.local host.    |  | | --- | | $host = Get-VBRServer -Name "esx09.tech.local"  $network = Get-VBRHvServerNetworkInfo -Server $host  New-VBRHvVirtualLabProxyAppliance -Server $host -EnableIPv4Interface -ObtainIPAutomatically -ObtainDNSAutomatically -Name "Proxy\_appliance\_05" -Network $network[3] |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $host variable. 2. Run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. Set the $host variable as the Server parameter value. Save the result to the $network variable. 3. Run the New-VBRHvVirtualLabProxyAppliance cmdlet. Specify the following settings:  * Set the $host variable as the Server parameter value. * Provide the EnableIPv4Interface parameter. * Provide the ObtainIPAutomatically parameter. * Provide the ObtainDNSAutomatically parameter. * Specify the Name parameter value. * Set the $network[3] variable as the Network parameter value.   The Get-VBRHvServerNetworkInfo cmdlet will return an array of production networks. Mind the ordinal number of the necessary production network (An array starts with 0. In our example, it is the fourth production network in the array). |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Defining Settings of Proxy Appliance as Proxy

|  |  |
| --- | --- |
| This example shows how to define settings of a proxy appliance that is deployed with the automatic IP and DNS and acts as an Internet proxy server. The proxy appliance will be deployed with the following settings:   * The proxy appliance will be deployed on the esx07.tech.local host. * VMs from the isolated network will use the 172.17.1.2 IP address to access the Internet. * VMs from isolated network will use this the 8085 port number to access the Internet.     |  | | --- | | $host = Get-VBRServer -Name "esx07.tech.local"  New-VBRHvVirtualLabProxyAppliance -Server $host -EnableIPv4Interface -ObtainIPAutomatically -ObtainDNSAutomatically -HTTPPort 8085 -ProductionProxyIPAddress 172.17.1.2 -EnableInternetProxy |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $host variable. 2. Run the New-VBRHvVirtualLabProxyAppliance cmdlet. Specify the following settings:  * Set the $host variable as the Server parameter value.  * Provide the EnableIPv4Interface parameter.  * Provide the ObtainIPAutomatically parameter. * Provide the ObtainDNSAutomatically parameter. * Specify the HTTPPort parameter value. * Specify the ProductionProxyIPAddress parameter value. * Provide the EnableInternetProxy parameter. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md)


