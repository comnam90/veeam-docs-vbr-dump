---
title: "VBRAzureComputeProxyAppliance"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrazurecomputeproxyappliance.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRAzureComputeProxyAppliance

In this article

Contains Azure proxy appliance settings.

Properties

| Property | Type | Description |
| --- | --- | --- |
| VMSize | [VBRAzureVMSize](vbrazurevmsize.md) | Size of the proxy appliance. |
| Network | [VBRAzureVirtualNetwork](vbrazurevirtualnetwork.md) | Network to which the proxy appliance appliance must be connected. |
| Subnet | [VBRAzureNetworkSubnet](vbrazurenetworksubnet.md) | Subnet for the proxy appliance. |
| ResourceGroup | [VBRAzureResourceGroup](vbrazureresourcegroup.md) | Resource group that will be associated with the proxy appliance. |
| RedirectorPort | int | The port that Veeam Backup & Replication will use to route requests between the proxy appliance and backup infrastructure components. |

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
