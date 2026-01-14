---
title: "Sync-VBRCloudTenantReplicationResources"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/sync-vbrcloudtenantteplicationresources.html"
last_updated: "10/7/2025"
product_version: "13.0.1.1071"
---

# Sync-VBRCloudTenantReplicationResources

In this article

Short Description

Refreshes information about current usage of the replication resources by a cloud tenant.

Applies to

Platform: VMware, Hyper-V

Product Edition: Standard, Enterprise, Enterprise Plus, Veeam Universal License

Syntax

This cmdlet provides parameter sets that allow you to:

* Update the information about the replication resource usage for a specific cloud tenant.

|  |
| --- |
| Sync-VBRCloudTenantReplicationResources -Tenant <VBRCloudTenant>  [<CommonParameters>] |

* Update the information about the replication resource usage for a specific hardware plan.

|  |
| --- |
| Sync-VBRCloudTenantReplicationResources [-ViHardwarePlan <VBRViCloudHardwarePlan>] [-HvHardwarePlan <VBRHvCloudHardwarePlan>]  [<CommonParameters>] |

Detailed Description

This cmdlet updates the information about the cloud tenant current usage of the replication resources. You can see the refreshed remaining replication resources in the user interface of Veeam Backup & Replication.

Parameters

| Parameter | Description | Type | Required | Position | Accept Pipeline Input |
| --- | --- | --- | --- | --- | --- |
| Tenant | Specifies the cloud tenant you want to refresh the replication resource usage numbers for. | Accepts the [VBRCloudTenant](vbrcloudtenant.md) object. To get this object, run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. | True | Named | True (ByValue, |
| HvHardwarePlan | [For Hyper-V environments] Specifies the hardware plan you want to refresh the replication resource usage numbers for. | Accepts the [VBRHvCloudHardwarePlan](vbrhvcloudhardwareplan.md) object. To get this object, run the [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) cmdlet. | False | Named | False |
| ViHardwarePlan | [For VMware environments] Specifies the hardware plan you want to refresh the replication resource usage numbers for. | Accepts the [VBRViCloudHardwarePlan](vbrvicloudhardwareplan.md) object. To get this object, run the [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md) cmdlet. | False | Named | False |

<CommonParameters>

This cmdlet supports Microsoft PowerShell common parameters. For more information on common parameters, see  [Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7).

Output Object

None.

Examples

Refreshing Information about Replication Resource Usage for Cloud Tenant

This example shows how to refresh the replication resource usage numbers for the ABC Company tenant.

|  |
| --- |
| $tenant = Get-VBRCloudTenant -Name "ABC Company"  Sync-VBRCloudTenantReplicationResources -Tenant $tenant |

Perform the following steps:

1. Run the [Get-VBRCloudTenant](get-vbrcloudtenant.md) cmdlet. Specify the Name parameter value. Save the result to the $tenant variable.
2. Run the Sync-VBRCloudTenantReplicationResources cmdlet. Set the $tenant variable as the Tenant parameter value.

Related Commands

* [Get-VBRCloudTenant](get-vbrcloudtenant.md)
* [Get-VBRCloudHardwarePlan](get-vbrcloudhardwareplan.md)

Page updated 10/7/2025

Page content applies to build 13.0.1.1071
