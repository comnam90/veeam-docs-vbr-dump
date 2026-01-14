---
title: "VBRCloudProviderReplicationResource"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrcloudproviderreplicationresource.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRCloudProviderReplicationResource

In this article

Contains replication resources provided under hardware plan.

Properties

| Property | Type | Description |
| --- | --- | --- |
| HardwarePlanName | string | Hardware plan name. |
| CPU | int32 | Quota of CPU resources assigned to the hardware plan (MHz). |
| Memory | int32 | Quota of memory resources assigned to the hardware plan (Mb). |
| Datastore | [VBRCloudProviderDatastore](vbrcloudproviderdatastore.md)[] | Array of datastores used for storing user data. |
| NetworkCount | int32 | Number of networks with or without access to the Internet assigned to the hardware plan. |
| PublicIpEnabled | bool | Indicates if the tenant is enabled to use the public IPs (TRUE) or not (FALSE). |
| PublicIp | string[] | Public IP addresses assigned to the tenant. |
| WanAcceleratorEnabled | bool | Indicates if the tenant is enabled to use a WAN accelerator (TRUE) or not (FALSE). |

Related Objects

[VBRCloudProvider](vbrcloudprovider.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
