---
title: "Set-VBRHvInstantRecoveryHelperAppliance"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrhvinstantrecoveryhelperappliance.html"
last_updated: "4/5/2024"
product_version: "13.0.1.1071"
---

# Set-VBRHvInstantRecoveryHelperAppliance

In this article

Short Description

Modifies settings for a helper appliance.

Applies to

Platform: Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

|  |
| --- |
| Set-VBRHvInstantRecoveryHelperAppliance -HelperAppliance <VBRHvInstantRecoveryHelperAppliance> [-Network <VBRHvServerNetworkInfo>] [-VLanID <Int32>] [-EnableIPv4Interface] [-ObtainIPAutomatically] [-IpAddress <IPAddress>] [-SubnetMask <IPAddress>] [-DefaultGateway <IPAddress>] [-ObtainDNSAutomatically] [-PreferredDNSServer <IPAddress>] [-AlternateDNSServer <IPAddress>] [-EnableIPv6Interface] [-ObtainIPv6AddressAutomatically] [-IPv6Address <IPAddress>] [-IPv6PrefixLength <Int32>] [-IPv6DefaultGateway <IPAddress>] [-ObtainIPv6DNSAutomatically] [-IPv6PreferredDNSServer <IPAddress>] [-IPv6AlternateDNSServer <IPAddress>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies settings of a helper appliance used in Instant Recovery to Microsoft Hyper-V.

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| HelperAppliance | Specifies a helper appliance which settings you want to modify. | Accepts the VBRHvInstantRecoveryHelperAppliance object. To create this object, run the [New-VBRHvInstantRecoveryHelperAppliance](new-vbrhvinstantrecoveryhelperappliance.md) cmdlet. | True | Named | True (ByPropertyName, ByValue) |
| Network | Specifies an array of production networks to which the helper appliance must be connected. | Accepts the VBRHvServerNetworkInfo[] object. To get this object, run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. | True | Named | False |
| VLanID | Specifies the VLAN ID where the helper appliance must reside. | int | False | Named | False |
| EnableIPv4Interface | Enables the option to use IPv4 addresses.  IPv4 is used by default. | SwitchParameter | False | Named | False |
| ObtainIPAutomatically | Use if you have a DHCP server in the network.  If you provide this parameter, Veeam Backup & Replication will obtain an IP address of the helper appliance automatically. | SwitchParameter | False | Named | False |
| IpAddress | For the ObtainIPAutomatically parameter set to False.  Specifies the IPv4 address of the helper appliance. | IPAddress | False | Named | False |
| SubnetMask | Specifies the subnet mask of the network where the helper appliance will be connected. | IPAddress | False | Named | False |
| DefaultGateway | Specifies the IPv4 address of the default gateway in the network where the appliance resides. | IPAddress | False | Named | False |
| ObtainDNSAutomatically | Use if you have a DHCP server in the network.  If you provide this parameter, Veeam Backup & Replication will obtain an IPv4 address of the DNS server automatically. | SwitchParameter | False | Named | False |
| PreferredDNSServer | Specifies the IPv4 address of the DNS server in the network where the appliance resides. | IPAddress | False | Named | False |
| AlternateDNSServer | Specifies the IPv4 address of an alternate DNS server in the network where the appliance resides. | IPAddress | False | Named | False |
| EnableIPv6Interface | Enables the option to use IPv6 addresses. | SwitchParameter | False | Named | False |
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

Change IP address settings of a helper appliance

This example shows how to modify IP address settings for a helper appliance.

|  |
| --- |
| $network = Get-VBRHvServerNetworkInfo -Server "srv01.tech.local"  $appliance = New-VBRHvInstantRecoveryHelperAppliance -Network $network  Set-VBRHvInstantRecoveryHelperAppliance -HelperAppliance $appliance -ObtainIPAutomatically |

Perform the following steps:

1. Run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. Specify the Server parameter. Save the result to the $network variable.
2. Run the [New-VBRHvInstantRecoveryHelperAppliance](new-vbrhvinstantrecoveryhelperappliance.md) cmdlet. Set the $network variable as the Network parameter value. Save the result to the $appliance variable.
3. Run the Set-VBRHvInstantRecoveryHelperAppliance cmdlet. Set the $appliance variable as the HelperAppliance parameter value. Provide the ObtainIPAutomatically parameter.

Page updated 4/5/2024

Page content applies to build 13.0.1.1071
