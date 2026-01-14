---
title: "Veeam Cloud Connect Replication Resources"
source_url: "https://helpcenter.veeam.com/docs/vbr/powershell/replication_resources.html"
last_updated: "4/24/2024"
product_version: "13.0.1.1071"
---

# Veeam Cloud Connect Replication Resources

In this article

Replication resources are quotas of resources for replication to the cloud. Replication resources include access to the service provider hardware, cloud storage and networking.

To provide a tenant with the replication resources, you need to run the [New-VBRCloudTenantReplicationResources](new-vbrcloudtenantreplicationresources.md) cmdlet. The replication resources include the following components:

1. [Hardware plan options](new-vbrcloudtenanthwplanoptions.md):

* [Hardware plan](hardware_plans.md)
* [Optional] [WAN acceleration](wan_cmdlets.md)

1. Failover resources.

The failover resources include using a network extension appliance that provides a network for the cloud replicas. See [Tenant Network Appliances](#network_appliances) to manage the network extension appliances.

1. [Public IP addresses](#public_ip).

Replication Resources

| Cmdlet | Operation |
| --- | --- |
| [New-VBRCloudTenantReplicationResources](new-vbrcloudtenantreplicationresources.md) | Creates a replication resources object |
| [New-VBRCloudTenantHwPlanOptions](new-vbrcloudtenanthwplanoptions.md) | Creates a hardware plan options object |
| [New-VBRvCDReplicationResource](new-vbrvcdreplicationresource.md) | Creates Cloud Director replication resource settings |
| [New-VBRvCDOrganizationvDCOptions](new-vbrvcdorganizationvdcoptions.md) | Creates Cloud Director Organizations settings |

Tenant Network Appliances

| Cmdlet | Operation |
| --- | --- |
| [Add-VBRCloudPublicIP](add-vbrcloudpublicip.md) | Creates a pool of public IP addresses |
| [Get-VBRCloudPublicIP](get-vbrcloudpublicip.md) | Returns existing public IP addresses |
| [Remove-VBRCloudPublicIP](remove-vbrcloudpublicip.md) | Removes public IP addresses |

Public IP Addresses

| Cmdlet | Operation |
| --- | --- |
| [Get-VBRCloudTenantNetworkAppliance](get-vbrcloudtenantnetworkappliance.md) | Returns tenants' network extension appliances |
| [Set-VBRCloudTenantNetworkAppliance](set-vbrcloudtenantnetworkappliance.md) | Modifies tenants' network extension appliances |

Page updated 4/24/2024

Page content applies to build 13.0.1.1071
