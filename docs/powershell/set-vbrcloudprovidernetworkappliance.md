---
title: "Set-VBRCloudProviderNetworkAppliance"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/set-vbrcloudprovidernetworkappliance.html"
last_updated: "12/19/2024"
product_version: "13.0.1.1071"
---

# Set-VBRCloudProviderNetworkAppliance

In this article

Short Description

Modifies network extension appliances on user side.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Modify an appliance with default settings.

|  |
| --- |
| Set-VBRCloudProviderNetworkAppliance -NetworkAppliance <VBRCloudProviderNetworkAppliance> [-Server <CHost>] [-Network <IVBRServerNetworkInfo>] [-IpAddress <string>] [-SubnetMask <string>] [-DefaultGateway <string>] [-Ipv6Address <string>] [-Ipv6PrefixLength <int32>] [-Ipv6DefaultGateway <string>] [-EnableIpv4Interface <bool>] [-EnableIpv6Interface <bool>] [-ObtainIpAddressAutomatically] [-ObtainIpv6AddressAutomatically]  [<CommonParameters>] |

* Modify the VMware appliance with advanced settings.

|  |
| --- |
| Set-VBRCloudProviderNetworkAppliance -NetworkAppliance <VBRCloudProviderNetworkAppliance> [-Server <CHost>] [-ResourcePool <CViResourcePoolItem>] [-Network <IVBRServerNetworkInfo>] [-IpAddress <string>] [-SubnetMask <string>] [-DefaultGateway <string>] [-Ipv6Address <string>] [-Ipv6PrefixLength <int32>] [-Ipv6DefaultGateway <string>] [-EnableIpv4Interface <bool>] [-EnableIpv6Interface <bool>] [-ObtainIpAddressAutomatically] [-ObtainIpv6AddressAutomatically] [-Datastore <VBRViDatastore>]  [<CommonParameters>] |

* Modify a Hyper-V appliance with advanced settings.

|  |
| --- |
| Set-VBRCloudProviderNetworkAppliance -NetworkAppliance <VBRCloudProviderNetworkAppliance> [-Server <CHost>] [-Network <IVBRServerNetworkInfo>] [-IpAddress <string>] [-SubnetMask <string>] [-DefaultGateway <string>] [-Ipv6Address <string>] [-Ipv6PrefixLength <int32>] [-Ipv6DefaultGateway <string>] [-EnableIpv4Interface <bool>] [-EnableIpv6Interface <bool>] [-ObtainIpAddressAutomatically] [-ObtainIpv6AddressAutomatically] [-Folder <string>] [-VLanId <int>]  [<CommonParameters>] |

Detailed Description

This cmdlet modifies a selected VMware or a Hyper-V network extension appliance on the user cloud host.

|  |
| --- |
| Important |
| To modify settings of a network extension appliance, you must save the result of the Set-VBRCloudProviderNetworkAppliance cmdlet to a variable. Otherwise, the settings of the appliance will remain unchanged. |

|  |
| --- |
| Note |
| To modify settings, specify new values for the necessary parameters. The cmdlet will overwrite the previous parameter values with new values. The parameters that you omit will remain unchanged. |

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| NetworkAppliance | Specifies the network appliance that you want to modify. | Accepts the  VBRCloudTenantNetworkAp appliance object. To get this object, run the [Get-VBRCloudTenantNetworkAppliance](get-vbrcloudtenantnetworkappliance.md) cmdlet. | True | Named | False |
| Server | The ESXi or a Hyper-V host where you want to create the appliance. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | False | Named | False |
| Network | Specifies the service provider network. The appliance will use this network to communicate between the user's production VMs and VM replicas on the cloud host. | Accepts the IVBRServerNetworkInfo object. To get this object, run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) or [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlets. | False | Named | False |
| IpAddress | Specifies the IP address. This address will be assigned to the appliance. | String | False | Named | False |
| SubnetMask | Specifies the subnet mask. This subnet mask will be used by the appliance. | String | False | Named | False |
| DefaultGateway | Specifies the default gateway. This gateway will be used by the appliance. | String | False | Named | False |
| Ipv6Address | Specifies the IPv6 address that you want to assign to the appliance. | String | False | Named | False |
| Ipv6PrefixLength | Specifies the length of an IPv6 prefix. | Int32 | False | Named | False |
| Ipv6DefaultGateway | Specifies the IPv6 address of the default gateway. The appliance will use this IP address. | String | False | Named | False |
| EnableIpv4Interface | Enables the IPv4 settings. If you provide this parameter, you will be able to specify the following settings.   * IPv4 address * Subnet mask * Default gateway   Note: If you set this parameter to :$False, you will not be able to specify the network settings manually. | Bool | False | Named | False |
| EnableIpv6Interface | Enables the IPv6 settings. If you provide this parameter, you will be able to specify the following settings.   * IPv6 address * The length of an IPv6 prefix * Default gateway   Note: If you set this parameter to :$False, you will not be able to specify the network settings manually. | Bool | False | Named | False |
| ObtainIpAddressAutomatically | Defines that the cmdlet will assign the IPv4 address automatically. | SwitchParameter | False | Named | False |
| ObtainIpv6AddressAutomatically | Defines that the cmdlet will assign the IPv6 address automatically. | SwitchParameter | False | Named | False |
| ResourcePool | Specifies the resource pool where you want to create the VMware appliance. | Accepts the  CViResourcePoolItem appliance object. To get this object, run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. | False | Named | False |
| Datastore | Specifies the datastore where you want to create the VMware appliance. | Accepts the  VBRViDatastore appliance object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| Folder | Specifies the folder where you want to create the Hyper-V appliance. | String | False | Named | False |
| VLanId | Specifies the VLAN network provided to the user by the hardware plan. The appliance will use this VLAN to connect to the service provider network. | Int | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

* [VBRViCloudProviderNetworkAppliance](vbrvicloudprovidernetworkappliance.md)
* [VBRHvCloudProviderNetworkAppliance](vbrhvcloudprovidernetworkappliance.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Modifying Resource Pool Settings for VMware Appliance

|  |  |
| --- | --- |
| This example shows how to change the resource pool for a VMware appliance created on the srv02.tech.local host.  |  | | --- | | $provider = Get-VBRCloudProvider –Name "104.45.95.227"  $viAppl = Get-VBRCloudProviderNetworkAppliance -CloudProvider $provider  $server = $viAppl.Host  $newResPool = Find-VBRViResourcePool -Name "ResourcePool\_05" -Server $server  $appliance = Set-VBRCloudProviderNetworkAppliance –NetworkAppliance $viAppl –ResourcePool $newResPool |  Perform the following steps:   1. Run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. Specify the Name parameter value. Save the result to the $provider variable. 2. Run the [Get-VBRCloudProviderNetworkAppliance](get-vbrcloudprovidernetworkappliance.md) cmdlet. Set the $provider variable as the CloudProvider parameter value. Save the result to the $viAppl variable. 3. Assign the $server variable the $viAppl.Host value. 4. Run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. Specify the Name and Server parameter values. Save the result to the $newResPool variable. 5. Run the Set-VBRCloudProviderNetworkAppliance cmdlet. Set the $viAppl variable as the NetworkAppliance parameter value. Set the $newResPool variable as the ResourcePool parameter value. Save the result to the $appliance variable. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Modifying Folder Settings for Hyper-V Appliance

|  |  |
| --- | --- |
| This example shows how to change the folder for a Hyper-V appliance created on the srv02.tech.local host.  |  | | --- | | $provider = Get-VBRCloudProvider –Name "104.45.95.227"  $viAppl = Get-VBRCloudProviderNetworkAppliance -CloudProvider $provider  $newFolder = “C:\Users\admin”  $appliance = Set-VBRCloudProviderNetworkAppliance –NetworkAppliance $hvAppl –Folder $newFolder |  Perform the following steps:   1. Run the [Get-VBRCloudProvider](get-vbrcloudprovider.md) cmdlet. Specify the Name parameter values. Save the result to the $provider variable. 2. Run the [Get-VBRCloudProviderNetworkAppliance](get-vbrcloudprovidernetworkappliance.md) cmdlet. Set the $provider variable as the CloudProvider parameter value. Save the result to the $viAppl variable. 3. Assign the $newFolder variable the C:\Users\admin value. 4. Run the Set-VBRCloudProviderNetworkAppliance cmdlet. Set the $hvAppl variable as the NetworkAppliance parameter value. Set the $newFolder variable as the Folder parameter value. Save the result to the $appliance variable. |

Related Commands

* [Get-VBRCloudProviderNetworkAppliance](get-vbrcloudprovidernetworkappliance.md)
* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md)
* [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md)
* [Find-VBRViResourcePool](find-vbrviresourcepool.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)

Page updated 12/19/2024

Page content applies to build 13.0.1.1071
