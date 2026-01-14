---
title: "VBRHvCloudProviderNetworkAppliance"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrhvcloudprovidernetworkappliance.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRHvCloudProviderNetworkAppliance

In this article

Contains Hyper-V network appliance on service provider side.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Folder | string | File path of the storage used by the appliance. |
| VLanId | int32 | VLAN ID. |
| Host | CHost | Server where the appliance is created. |
| Network | IVBRServerNetworkInfo | Network to which the appliance is connected. |
| IpAddress | string | Appliance IP address. |
| SubnetMask | string | Appliance subnet mask. |
| DefaultGateway | string | Default gateway used by the appliance. |
| Platform | [VBRPlatform](veeam_powershell_types.md#vbrplatform) | Virtualization platform: Hyper-V. |
| ObtainIpAddressAutomatically | bool | Indicates if the IP address of the appliance is assigned automatically (TRUE) or user-defined (FALSE). |
| Name | string | Appliance name. |
| Id | GUID | Appliance ID. |

Related Commands

[Network Appliance](user_network_appliance.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
