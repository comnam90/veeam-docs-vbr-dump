---
title: "VBRCloudTenantHwPlanOptions"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/vbrcloudtenanthwplanoptions.html"
last_updated: "11/6/2023"
product_version: "13.0.1.1071"
---

# VBRCloudTenantHwPlanOptions

In this article

Contains options of hardware plan assigned to tenant.

Properties

| Property | Type | Description |
| --- | --- | --- |
| HardwarePlan | VBRCloudHardwarePlan | Hardware plan to which the tenant is subscribed. |
| WanAcceleratorEnabled | bool | Indicates if WAN accelerator is enabled (TRUE) or not (FALSE). |
| WanAccelerator | [CWanAccelerator](cwanaccelerator.md) | WAN accelerator allocated to the tenant. |
| UsedCPU | int | Amount of a number of CPU resources allocated to the tenant. |
| UsedMemory | int | Amount of storage allocated to the tenant in MB. |
| DatastoreQuota | [VBRCloudDatastoreQuota](vbrclouddatastorequota.md)[] | Datastore quota allocated to the tenant. |

Related Commands

[New-VBRCloudTenantHwPlanOptions](new-vbrcloudtenanthwplanoptions.md)

Page updated 11/6/2023

Page content applies to build 13.0.1.1071
