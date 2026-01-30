---
title: "New-VBRHvInstantRecoveryHelperAppliance"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrhvinstantrecoveryhelperappliance.html"
last_updated: "4/4/2024"
product_version: "13.0.1.1071"
---

# New-VBRHvInstantRecoveryHelperAppliance


Short Description

Defines settings for a helper appliance.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| New-VBRHvInstantRecoveryHelperAppliance -Network <VBRHvServerNetworkInfo> [-VLanID <int>] [-EnableIPv4Interface] [-ObtainIPAutomatically] [-IpAddress <ipaddress>] [-SubnetMask <ipaddress>] [-DefaultGateway <ipaddress>] [-ObtainDNSAutomatically] [-PreferredDNSServer <ipaddress>] [-AlternateDNSServer <ipaddress>] [-EnableIPv6Interface] [-ObtainIPv6AddressAutomatically] [-IPv6Address <ipaddress>] [-IPv6PrefixLength <int>] [-IPv6DefaultGateway <ipaddress>] [-ObtainIPv6DNSAutomatically] [-IPv6PreferredDNSServer <ipaddress>] [-IPv6AlternateDNSServer <ipaddress>]  [<CommonParameters>] |

Detailed Description

This cmdlet defines the VBRHvInstantRecoveryHelperAppliance object. This object contains settings for a helper appliance used in Instant Recovery to Microsoft Hyper-V.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Network | Specifies an array of production networks to which the helper appliance must be connected. | Accepts the VBRHvServerNetworkInfo[] object. To get this object, run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. | True | Named | False |
| VLanID | Specifies the VLAN ID where the helper appliance must reside. | int | False | Named | False |
| EnableIPv4Interface | If you provide this parameter Veeam Backup & Replication will use IPv4 addresses.  IPv4 is used by default. | SwitchParameter | False | Named | False |
| ObtainIPAutomatically | Use if you have a DHCP server in the network.  If you provide this parameter, Veeam Backup & Replication will obtain an IP address of the helper appliance automatically. | SwitchParameter | False | Named | False |
| IpAddress | For the ObtainIPAutomatically parameter set to False.  Specifies the IPv4 address of the helper appliance. | IPAddress | False | Named | False |
| SubnetMask | Specifies the subnet mask of the network where the helper appliance will be connected. | IPAddress | False | Named | False |
| DefaultGateway | Specifies the IPv4 address of the default gateway in the network where the appliance resides. | IPAddress | False | Named | False |
| ObtainDNSAutomatically | Use if you have a DHCP server in the network.  If you provide this parameter, Veeam Backup & Replication will obtain an IPv4 address of the DNS server automatically. | SwitchParameter | False | Named | False |
| PreferredDNSServer | Specifies the IPv4 address of the DNS server in the network where the appliance resides. | IPAddress | False | Named | False |
| AlternateDNSServer | Specifies the IPv4 address of an alternate DNS server in the network where the appliance resides. | IPAddress | False | Named | False |
| EnableIPv6Interface | If you provide this parameter Veeam Backup & Replication will use IPv6 addresses. | SwitchParameter | False | Named | False |
| ObtainIPv6AddressAutomatically | Use if you have a DHCP server in the network.  If you provide this parameter, Veeam Backup & Replication will obtain an IPv6 address of the helper appliance automatically. | SwitchParameter | False | Named | False |
| IPv6Address | For the EnableIPv6Interface parameter specified and the ObtainIPAutomatically parameter set to False.  If you provide this parameter Veeam Backup & Replication will use IPv6 addresses. | IPAddress | False | Named | False |
| IPv6PrefixLength | For the EnableIPv6Interface parameter specified and the ObtainIPAutomatically parameter set to False.  Specifies the length of the IPv6 prefix. | int | False | Named | False |
| IPv6DefaultGateway | For the EnableIPv6Interface parameter specified and the ObtainIPAutomatically parameter set to False.  Specifies the IPv6 address of the default gateway in the network where the appliance resides. | IPAddress | False | Named | False |
| ObtainIPv6DNSAutomatically | For the EnableIPv6Interface parameter specified and the ObtainIPAutomatically parameter set to False.  Use if you have a DHCP server in the network.  If you provide this parameter, Veeam Backup & Replication will obtain an IPv6 address of the DNS server automatically. | SwitchParameter | False | Named | False |
| IPv6PreferredDNSServer | For the EnableIPv6Interface parameter specified and the ObtainIPAutomatically parameter set to False.  Specifies the IPv6 address of the DNS server in the network where the appliance resides. | IPAddress | False | Named | False |
| IPv6AlternateDNSServer | For the EnableIPv6Interface parameter specified and the ObtainIPAutomatically parameter set to False.  Specifies the IPv6 address of the alternate DNS server in the network where the appliance resides. | IPAddress | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

The cmdlet returns the VBRHvInstantRecoveryHelperAppliance object that defines helper appliance settings.

Examples

Configure network for an appliance

This example shows how to configure a network for a helper appliance used in Instant Recovery to Microsoft Hyper-V.

|  |
| --- |
| $network = Get-VBRHvServerNetworkInfo -Server "srv01.tech.local"  New-VBRHvInstantRecoveryHelperAppliance -Network $network |

Perform the following steps:

1. Run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. Specify the Server parameter value. Save the result to the $network variable.
2. Run the New-VBRHvInstantRecoveryHelperAppliance cmdlet. Set the $network variable as the Network parameter value.


