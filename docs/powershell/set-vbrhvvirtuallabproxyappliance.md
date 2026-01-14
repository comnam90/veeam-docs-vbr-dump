---
title: "Set-VBRHvVirtualLabProxyAppliance"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrhvvirtuallabproxyappliance.html"
last_updated: "5/2/2024"
product_version: "13.0.1.1071"
---

# Set-VBRHvVirtualLabProxyAppliance

In this article

Short Description

Modifies settings of proxy appliances for Hyper-V virtual lab.

Applies to

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRHvVirtualLabProxyAppliance -ProxyAppliance <VBRHvVirtualLabProxyAppliance> [-Network <VBRHvServerNetworkInfo>] [-VLanID <int>] [-EnableIPv4Interface] [-ObtainIPAutomatically] [-IPAddress <ipaddress>] [-SubnetMask <string>] [-DefaultGateway <ipaddress>] [-ObtainDNSAutomatically] [-PreferredDNSServer <ipaddress>] [-AlternateDNSServer <ipaddress>] [-EnableIPv6Interface] [-ObtainIPv6AddressAutomatically] [-IPv6Address <ipaddress>] [-IPv6PrefixLength <int>] [-IPv6DefaultGateway <ipaddress>] [-ObtainIPv6DNSAutomatically] [-IPv6PreferredDNSServer <ipaddress>] [-IPv6AlternateDNSServer <ipaddress>] [-HTTPPort <int>] [-ProductionProxyIPAddress <ipaddress>] [-EnableInternetProxy]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of Hyper-V virtual lab proxy appliances.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| ProxyAppliance | Specifies a proxy appliance that you want to modify. | Accepts the VBRHvVirtualLabProxyAppliance object. To create this object, run the [New-VBRHvVirtualLabProxyAppliance](new-vbrhvvirtuallabproxyappliance.md) cmdlet. | True | Named | True (ByValue, |
| Network | Specifies the production network. The cmdlet will connect a proxy appliance to the specified network. | Accepts the VBRHvServerNetworkInfo object. To get this object, run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. | False | Named | False |
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
| IPv6Address | Specifies an IPv6 address for a proxy appliance in the production network. The cmdlet will assign this IP address to a proxy appliance. | IPAddress | False | Named | False |
| IPv6PrefixLength | Specifies a prefix length for a proxy appliance in the production network. The cmdlet will set up network settings of a proxy appliance with this prefix length. | String | False | Named | False |
| IPv6DefaultGateway | Specifies an IPv6 address of a default gateway. The cmdlet will assign this IP address to a default gateway on a proxy appliance. | IPAddress | False | Named | False |
| ObtainIPv6DNSAutomatically | Defines that a proxy appliance will obtain IPv6 DNS server settings automatically.  If you provide this parameter, Veeam Backup & Replication will obtain DNS server settings for the proxy appliance automatically. Otherwise, you will need to set the DNS server settings manually. | SwitchParameter | False | Named | False |
| IPv6PreferredDNSServer | Specifies an IPv6 address of a preferred DNS server. | IPAddress | False | Named | False |
| IPv6AlternateDNSServer | Specifies an IPv6 address of an alternate DNS server. | IPAddress | False | Named | False |
| HTTPPort | Specifies the port number. VMs from the isolated network will use this port number to access the Internet.  Default: 8080. | Int32 | False | Named | False |
| ProductionProxyIPAddress | Specifies an IP address or a fully qualified domain name of an Internet-facing proxy server that VMs from the isolated network must use to access the Internet. | IPAddress | False | Named | False |
| EnableInternetProxy | Defines that a proxy appliance will act as an internet proxy for VMs in the isolated network.  If you provide this parameter, a proxy appliance will act as an internet proxy for VMs in the isolated network. Otherwise, VMs from the isolated network will not have access to the Internet. | SwitchParameter | False | Named | False |
| VLanID | Specifies an ID of an isolated network. The cmdlet will create the isolated network with the specified ID. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRHvVirtualLabProxyAppliance object that defines settings of proxy appliances that are added to the Hyper-V virtual lab.

Examples

Enabling IPv6 Interface for Proxy Appliance

This example shows how to enable IPv6 interface for the proxy appliance named Proxy\_appliance\_05. The proxy appliance will have both IPv4 and IPv6 interfaces enabled.

|  |
| --- |
| $host = Get-VBRServer -Name "esx09.tech.local"  $network = Get-VBRHvServerNetworkInfo -Server $host  $proxyapp = New-VBRHvVirtualLabProxyAppliance -Server $host -EnableIPv4Interface -ObtainIPAutomatically -ObtainDNSAutomatically -Name "Proxy\_appliance\_05" -Network $network[3]  Set-VBRHvVirtualLabProxyAppliance -ProxyAppliance $proxyapp -EnableIPv6Interface -ObtainIPv6AddressAutomatically -ObtainIPv6DNSAutomatically |

Perform the following steps:

1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Specify the Name parameter value. Save the result to the $host variable.
2. Run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. Set the $host variable as the Server parameter value. Save the result to the $network variable.
3. Run the [New-VBRHvVirtualLabProxyAppliance](new-vbrhvvirtuallabproxyappliance.md) cmdlet. Specify the Server, EnableIPv4Interface, ObtainIPAutomatically, ObtainDNSAutomatically, Name and Network parameter values. Save the result to the $proxyapp variable.
4. Run the Set-VBRHvVirtualLabProxyAppliance cmdlet. Specify the following settings:

* Set the $proxyapp variable as the ProxyAppliance parameter value.
* Provide the EnableIPv6Interface parameter.
* Provide the ObtainIPv6AddressAutomatically parameter.
* Provide the ObtainIPv6DNSAutomatically parameter.

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md)
* [New-VBRHvVirtualLabProxyAppliance](new-vbrhvvirtuallabproxyappliance.md)

Page updated 5/2/2024

Page content applies to build 13.0.1.1071
