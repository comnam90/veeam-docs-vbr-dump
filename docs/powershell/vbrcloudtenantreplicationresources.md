---
title: "VBRCloudTenantReplicationResources"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrcloudtenantreplicationresources.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRCloudTenantReplicationResources

In this article

Contains replication resources assigned to tenant.

Properties

| Property | Type | Description |
| --- | --- | --- |
| NetworkFailoverResourcesEnabled | bool | Indicates if network resources are allocated to the tenant (TRUE) or not (FALSE). |
| HardwarePlanOptions | [VBRCloudTenantHwPlanOptions](vbrcloudtenanthwplanoptions.md)[] | Hardware plan options assigned to the tenant. |
| PublicIpEnabled | bool | Indicates if the tenant is enabled to use the public IPs (TRUE) or not (FALSE). |
| NumberOfPublicIp | int | Number of public IPs assigned to the tenant. |
| TenantNetworkAppliance | [VBRCloudTenantNetworkAppliance](vbrcloudtenantnetworkappliance.md)[] | Tenant network helper appliances. |

Related Commands

[New-VBRCloudTenantReplicationResources](new-vbrcloudtenantreplicationresources.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
