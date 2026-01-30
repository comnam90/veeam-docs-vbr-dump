---
title: "VBRViCloudProviderNetworkAppliance"
product: "vbr"
doc_type: "powershell"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrvicloudprovidernetworkappliance.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRViCloudProviderNetworkAppliance


Contains VMware network appliance on service provider side.

Properties

| Property | Type | Description |
| --- | --- | --- |
| Datastore | VBRViDatastore | Datastore used by the appliance. |
| ResourcePool | CViResourcePoolItem | Resource pool used by the appliance. |
| Host | CHost | Server where the appliance is created. |
| Network | IVBRServerNetworkInfo | Network to which the appliance is connected. |
| IpAddress | string | IP address of the appliance. |
| SubnetMask | string | Subnet mask assigned to the appliance. |
| DefaultGateway | string | Default gateway used by the appliance. |
| Platform | 3 | Virtualization platform: VMware. |
| ObtainIpAddressAutomatically | bool | Indicates if the IP address of the appliance is assigned automatically (TRUE) or user-defined (FALSE). |
| Name | string | Appliance name. |
| Id | GUID | Appliance ID. |

Related Commands

[Network Appliance](user_network_appliance.md)


