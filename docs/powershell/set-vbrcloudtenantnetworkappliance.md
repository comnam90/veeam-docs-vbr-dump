---
title: "Set-VBRCloudTenantNetworkAppliance"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcloudtenantnetworkappliance.html"
last_updated: "5/17/2024"
product_version: "13.0.1.1071"
---

# Set-VBRCloudTenantNetworkAppliance

In this article

Short Description

Modifies a network extension appliance.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Requires a VCP license.

Syntax

|  |
| --- |
| Set-VBRCloudTenantNetworkAppliance -Appliance <VBRCloudTenantNetworkAppliance> [-Name <string>] [-ProductionNetwork <IVBRServerNetworkInfo>] [-IpAddress <ipaddress>] [-DefaultGateway <ipaddress>] [-Ipv6Address <ipaddress>] [-Ipv6PrefixLength <string>] [-Ipv6DefaultGateway <ipaddress>] [-EnableIpv4Interface <bool>] [-EnableIpv6Interface <bool>] [-ObtainIpAddressAutomatically] [-ObtainIpv6AddressAutomatically] [-SubnetMask <string>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies a network extension appliance. You can modify the network extension appliance for the cloud tenants of the following types:

* Simple cloud tenant accounts
* Cloud Director tenant accounts

|  |
| --- |
| Important |
| The cmdlets in this section operate only with the network appliances created by service providers.  To create a network appliance, a service provider must run the [New-VBRCloudTenantReplicationResources](new-vbrcloudtenantreplicationresources.md) cmdlet and provide the EnableNetworkFailoverResources parameter. The cmdlet will create a network appliance with the IPv4 and IPv6 addresses enabled by default. |

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Appliance | Specifies the network appliance you want to modify. | Accepts the [VBRCloudTenantNetworkAppliance](vbrcloudtenantnetworkappliance.md) object. To get this object, run the [Get-VBRCloudTenantNetworkAppliance](get-vbrcloudtenantnetworkappliance.md) cmdlet. | True | Named | True (ByValue, |
| Name | Specifies a name of the network appliance. | String | False | Named | False |
| ProductionNetwork | Specifies the network. The appliance will be connected to this network. | IVBRServerNetworkInfo | False | Named | False |
| IpAddress | Specifies the IPv4 address that you want to assign to the appliance. | IPAddress | False | Named | False |
| DefaultGateway | Specifies the IPv4 address of the default gateway. The appliance will use this IP address. | IPAddress | False | Named | False |
| Ipv6Address | Specifies the IPv6 address that you want to assign to the appliance. | IPAddress | False | Named | False |
| Ipv6PrefixLength | Specifies the length of an IPv6 prefix. | String | False | Named | False |
| Ipv6DefaultGateway | Specifies the IPv6 address of the default gateway. The appliance will use this IP address. | IPAddress | False | Named | False |
| EnableIpv4Interface | Enables the IPv4 settings. If you provide this parameter, you will be able to specify the following settings.   * IPv4 address * Subnet mask * Default gateway   Note: If you set this parameter to :$False, you will not be able to specify the network settings manually. | Boolean | False | Named | False |
| EnableIpv6Interface | Enables the IPv6 settings. If you provide this parameter, you will be able to specify the following settings.   * IPv6 address * The length of an IPv6 prefix * Default gateway   Note: If you set this parameter to :$False, you will not be able to specify the network settings manually. | Boolean | False | Named | False |
| ObtainIpAddressAutomatically | Defines that the cmdlet will assign the IPv4 address automatically. | SwitchParameter | False | Named | False |
| ObtainIpv6AddressAutomatically | Defines that the cmdlet will assign the IPv6 address automatically. | SwitchParameter | False | Named | False |
| SubnetMask | Specifies a subnet mask for IPv4 address. | String | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

[VBRCloudTenantNetworkAppliance](vbrcloudtenantnetworkappliance.md)

Examples

Modifying IPv4 Settings of Network Appliance

This example shows how to modify the Cloud Appliance for ABC Company network appliance settings. The cmdlet will modify the IPv4 address, subnet mask and the default gateway settings.

|  |
| --- |
| $appliance = Get-VBRCloudTenantNetworkAppliance –Name “Cloud Appliance for ABC Company”  Set-VBRCloudTenantNetworkAppliance –Appliance $appliance –Name "New Cloud Appliance for ABC Company" -EnableIpv4Interface:$True –IpAddress 172.15.15.10 –SubnetMask 255.255.255.0 –DefaultGateway 172.15.15.1 |

Perform the following steps:

1. Run the [Get-VBRCloudTenantNetworkAppliance](get-vbrcloudtenantnetworkappliance.md) cmdlet. Specify the Name parameter values. Save the result to the $appliance variable.
2. Run the Set-VBRCloudTenantNetworkAppliance cmdlet. Specify the following settings:

* Set the $appliance variable as the Appliance parameter value.
* Specify the Name parameter value.
* Provide the EnableIpv4Interface parameter and set its value to :$True.
* Specify the IpAddress parameter value.
* Specify the SubnetMask parameter value.
* Specify the DefaultGateway parameter value..

Related Commands

* [Get-VBRCloudTenantNetworkAppliance](get-vbrcloudtenantnetworkappliance.md)
* [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md)
* [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md)

Page updated 5/17/2024

Page content applies to build 13.0.1.1071
