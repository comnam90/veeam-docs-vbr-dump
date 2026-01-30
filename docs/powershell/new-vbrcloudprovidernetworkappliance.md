---
title: "New-VBRCloudProviderNetworkAppliance"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/new-vbrcloudprovidernetworkappliance.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# New-VBRCloudProviderNetworkAppliance


Short Description

Creates a network extension appliance on the user side.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Create an appliance with default settings.

|  |
| --- |
| New-VBRCloudProviderNetworkAppliance -Server <CHost> [-Network <IVBRServerNetworkInfo>] [-IpAddress <String>] [-SubnetMask <String>] [-DefaultGateway <String>] [-Ipv6Address <String>] [-Ipv6PrefixLength <Int32>] [-Ipv6DefaultGateway <String>] [-EnableIpv4Interface <Boolean>] [-EnableIpv6Interface <Boolean>] [-ObtainIpAddressAutomatically] [-ObtainIpv6AddressAutomatically]  [<CommonParameters>] |

* Create a VMware appliance with advanced settings.

|  |
| --- |
| New-VBRCloudProviderNetworkAppliance -Server <CHost> [-ResourcePool <CViResourcePoolItem>] [-Network <IVBRServerNetworkInfo>] [-IpAddress <String>] [-SubnetMask <String>] [-DefaultGateway <String>] [-Ipv6Address <String>] [-Ipv6PrefixLength <Int32>] [-Ipv6DefaultGateway <String>] [-EnableIpv4Interface <Boolean>] [-EnableIpv6Interface <Boolean>] [-ObtainIpAddressAutomatically] [-ObtainIpv6AddressAutomatically] [-Datastore <VBRViDatastore>]  [<CommonParameters>] |

* Create a Hyper-V appliance with advanced settings.

|  |
| --- |
| New-VBRCloudProviderNetworkAppliance -Server <CHost> [-Network <IVBRServerNetworkInfo>] [-IpAddress <String>] [-SubnetMask <String>] [-DefaultGateway <String>] [-Ipv6Address <String>] [-Ipv6PrefixLength <Int32>] [-Ipv6DefaultGateway <String>] [-EnableIpv4Interface <Boolean>] [-EnableIpv6Interface <Boolean>] [-ObtainIpAddressAutomatically] [-ObtainIpv6AddressAutomatically] [-Folder <String>] [-VLanId <Int32>]  [<CommonParameters>] |

Detailed Description

This cmdlet creates a VMware or a Hyper-V network extension appliance on the user's host. This appliance is applied in the cloud provider settings (see [Managing Service Provider](manage_sp.md)).

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Server | The ESXi or a Hyper-V host where the VMs you want to replicate locate. The network appliance will be created on this host. | Accepts the CHost object. To get this object, run the [Get-VBRServer](get-vbrserver.md) cmdlet. | True | Named | False |
| Network | Specifies the service provider network. The appliance will use this network to communicate between the user's production VMs and VM replicas on the cloud host. | Accepts the IVBRServerNetworkInfo object. To get this object, run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) or [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlets. | False | Named | False |
| IpAddress | Specifies the IP address. This address will be assigned to the appliance. | String | False | Named | False |
| SubnetMask | Specifies the subnet mask. This subnet mask will be used by the appliance. | String | False | Named | False |
| DefaultGateway | Specifies the default gateway. This gateway will be used by the appliance. | String | False | Named | False |
| Ipv6Address | Specifies the IPv6 address that you want to assign to the appliance. | String | False | Named | False |
| Ipv6PrefixLength | Specifies the length of an IPv6 prefix. | Int32 | False | Named | False |
| Ipv6DefaultGateway | Specifies the IPv6 address of the default gateway. The appliance will use this IP address. | String | False | Named | False |
| EnableIpv4Interface | Enables the IPv4 settings. If you provide this parameter, you will be able to specify the following settings.   * IPv4 address * Subnet mask * Default gateway   Note:   * To disable the IPv4 settings, set the EnableIpv4Interface parameter to $False. In this case, you will not be able to specify the network settings manually. * To enable IPv4 settings, set the EnableIpv4Interface parameter to $True. | Boolean | False | Named | False |
| EnableIpv6Interface | Enables the IPv6 settings. If you provide this parameter, you will be able to specify the following settings.   * IPv6 address * The length of an IPv6 prefix * Default gateway   Note:   * To disable the IPv6 settings, set the EnableIpv6Interface parameter to $False. In this case, you will not be able to specify the network settings manually. * To enable IPv6 settings, set the EnableIpv6Interface parameter to $True. | Boolean | False | Named | False |
| ObtainIpAddressAutomatically | Defines that the cmdlet will assign the IPv4 address automatically. | SwitchParameter | False | Named | False |
| ObtainIpv6AddressAutomatically | Defines that the cmdlet will assign the IPv6 address automatically. | SwitchParameter | False | Named | False |
| ResourcePool | Specifies the resource pool where you want to create the VMware appliance. | Accepts the CViResourcePoolItem object. To get this object, run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. | False | Named | False |
| Datastore | Specifies the datastore where you want to create the VMware appliance. | Accepts the VBRViDatastore object. To get this object, run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. | False | Named | False |
| Folder | Specifies the folder where you want to create the Hyper-V appliance. | String | False | Named | False |
| VLanId | Specifies the VLAN network provided to the user by the hardware plan. The appliance will use this VLAN to connect to the service provider network. | Int32 | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

* [VBRViCloudProviderNetworkAppliance](vbrvicloudprovidernetworkappliance.md)
* [VBRHvCloudProviderNetworkAppliance](vbrhvcloudprovidernetworkappliance.md)

Examples

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 1. Creating VMware Appliance with Advanced Settings [Using Variables]

|  |  |
| --- | --- |
| This example shows how to create a VMware appliance with advanced settings on the srv01.tech.local host.  |  | | --- | | $server = Get-VBRServer –Type ESXi -Name "srv01.tech.local"  $network = Get-VBRViServerNetworkInfo -Server $server | Where { $\_.NetworkName -eq "VM Network" }  $respool = Find-VBRViResourcePool -Server $server -Name "ResourcePool\_01"  $datastore = Find-VBRViDatastore -Server $server –Name "NOPDatastore"  $viAppl = New-VBRCloudProviderNetworkAppliance -Server $server -Network $network -ResourcePool $respool -Datastore $datastore |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Set the ESXi option for the Type parameter. Specify the Name parameter value. Save the server to the $server variable. 2. Run the [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md) cmdlet. Pass the result to the [Where-Object](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/where-object?view=powershell-7.3&viewFallbackFrom=powershell-7.1) cmdlet to select the networks with the NetworkName property that equals VM Network. Save the network to the $network variable. 3. Run the [Find-VBRViResourcePool](find-vbrviresourcepool.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. Save the resource pool to the $respool variable. 4. Run the [Find-VBRViDatastore](find-vbrvidatastore.md) cmdlet. Set the $server variable as the Server parameter value. Specify the Name parameter value. Save the datastore to the $datastore variable. 5. Run the New-VBRCloudProviderNetworkAppliance cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value. * Set the $network variable as the Network parameter value. * Set the $respool variable as the ResourcePool parameter value. * Set the $datastore variable as the Datastore parameter value. * Save the result to the $viAppl variable for future use. |

![](//img.veeam.com/helpcenter/baggage/arrow_next.svg)Example 2. Creating Hyper-V Appliance with Advanced Settings [Using Variables]

|  |  |
| --- | --- |
| This example shows how to create a Hyper-V appliance with advanced settings on the srv02.tech.local host.  |  | | --- | | $server = Get-VBRServer –Type HvServer -Name "srv02.tech.local"  $folder = "C:\Datastore"  $network = Get-VBRHvServerNetworkInfo -Server $server  | Where { $\_.NetworkName -eq "VM Network" }  $hvAppl = New-VBRCloudProviderNetworkAppliance -Server $server -Network $network –Folder $folder |  Perform the following steps:   1. Run the [Get-VBRServer](get-vbrserver.md) cmdlet. Set the HvServer option for the Type parameter. Specify the Name parameter value. Save the server to the $server variable. 2. Assign the $folder variable the C:\Datastore value. 3. Run the [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md) cmdlet. Set the $server variable as the Server parameter value and use the [Where-Object](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/where-object?view=powershell-7.3&viewFallbackFrom=powershell-7.1) statement to filter the networks by the .NetworkName property. Save the network to the $network variable. 4. Run the New-VBRCloudProviderNetworkAppliance cmdlet. Specify the following settings:  * Set the $server variable as the Server parameter value. * Set the $network variable as the Network parameter value. * Set the $folder variable as the Folder parameter value. * Save the result to the $hvAppl variable for future use. |

Related Commands

* [Get-VBRServer](get-vbrserver.md)
* [Get-VBRHvServerNetworkInfo](get-vbrhvservernetworkinfo.md)
* [Get-VBRViServerNetworkInfo](get-vbrviservernetworkinfo.md)
* [Find-VBRViResourcePool](find-vbrviresourcepool.md)
* [Find-VBRViDatastore](find-vbrvidatastore.md)


