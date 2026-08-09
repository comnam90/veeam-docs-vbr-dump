---
title: "/cloud/tenants/{ID}/vCloudComputeResources/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloud_tenants_id_vcloudcomputeresources_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cloud/tenants/{ID}/vCloudComputeResources/{ID}


Represents an organization VDC with the specified ID that is assigned to the tenant account with the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}/vCloudComputeResources/{ID} |

Related Resources

* [/cloud/tenants/{ID}](tenants_id.md)
* [/cloud/tenants/{ID}/vCloudComputeResources](cloud_tenants_id_vcloudcomputeresources.md)

Methods

The following methods are supported for the /cloud/tenants/{ID}/vCloudComputeResources/{ID} resource:

* [GET /cloud/tenants/{ID}/vCloudComputeResources/{ID}](get_cloud_tenants_id_vcloudcomputeresources_id.md)
* [DELETE /cloud/tenants/{ID}/vCloudComputeResources/{ID}](delete_cloud_tenants_id_vcloudcomputeresources_id.md)

Resource Representation

The /cloud/tenants/{ID}/vCloudComputeResources/{ID} resource has a resource representation of the following type.

|  |
| --- |
| <CloudTenantVCloudComputeResource Href="http://restapiem.tech.local:9399/api/cloud/tenants/59aa38fb-aa88-4656-bc52-d31e8f85083e/vcloudcomputeresources/c20a16a7-2d09-4374-850d-84b1d6c9f7f3" Type="CloudTenantVCloudComputeResource" Id="c20a16a7-2d09-4374-850d-84b1d6c9f7f3" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Links>     <Link Href="http://restapiem.tech.local:9399/api/cloud/tenants/59aa38fb-aa88-4656-bc52-d31e8f85083e/vcloudcomputeresources/c20a16a7-2d09-4374-850d-84b1d6c9f7f3" Rel="Delete"/>     <Link Href="http://restapiem.tech.local:9399/api/cloud/tenants/59aa38fb-aa88-4656-bc52-d31e8f85083e?format=Entity" Name="restapi" Type="CloudTenant" Rel="Up"/>     <Link Href="http://restapiem.tech.local:9399/api/backupServers/6b6456ca-68ac-4559-a0e9-808bb519082f?format=Entity" Name="restapivbr.tech.local" Type="BackupServer" Rel="Up"/>   </Links>   <VirtualDataCenterName>restapivdc01</VirtualDataCenterName>   <VirtualDataCenterRef>urn:vCloud:OrgVdc:1e902b80-e842-41e6-a4bf-4cf153c53e5c.urn:vcloud:vdc:c20a16a7-2d09-4374-850d-84b1d6c9f7f3</VirtualDataCenterRef>   <Enabled>true</Enabled>   <AllocationModel>AllocationPool</AllocationModel>   <UseNetworkFailoverResources>true</UseNetworkFailoverResources>   <ResourceUsage>     <CpuUsageMhz>0</CpuUsageMhz>     <MemoryUsageMb>0</MemoryUsageMb>     <StorageUsageGb>0</StorageUsageGb>   </ResourceUsage>   <WanAcceleratorUid>urn:veeam:WanAccelerator:9253bc8b-ab04-4f48-be35-08c81795d2e5</WanAcceleratorUid>   <NetworkAppliance>     <Name>Network Extension Appliance</Name>     <ProductionNetwork>VM Network</ProductionNetwork>     <ObtainIPAddressAutomatically>true</ObtainIPAddressAutomatically>     <ViDistributedSwitchUuid/>     <ProductionNetworkUnderDvs>false</ProductionNetworkUnderDvs>   </NetworkAppliance> </CloudTenantVCloudComputeResource> |

Page updated 2026-07-29

