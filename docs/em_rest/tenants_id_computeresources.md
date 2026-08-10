---
title: "/cloud/tenants/{ID}/computeResources"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/tenants_id_computeresources.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cloud/tenants/{ID}/computeResources


Represents a list of hardware plans to which the tenant account with the specified ID is subscibed.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}/computeResources |

Related Resources

* [/cloud/tenants/{ID}](tenants_id.md)
* [/cloud/tenants/{ID}/computeResources/{ID}](tenants_id_computeresources_id.md)

Methods

The following methods are supported for the /cloud/tenants/{ID}/computeResources resource:

* [GET /cloud/tenants/{ID}/computeResources](get_tenants_id_computeresources.md)
* [POST /cloud/tenants/{ID}/computeResources](post_tenants_id_computeresources.md)

Resource Representation

The /cloud/tenants/{ID}/computeResources resource has a resource representation of the following type.

|  |
| --- |
| <CloudTenantComputeResources xmlns="http://www.veeam.com/ent/v1.0">   <CloudTenantComputeResource Type="CloudTenantComputeResource" Href="https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7/computeResources/25f485fd-06e3-4ee2-9703-465c4d8c2fae" Id="25f485fd-06e3-4ee2-9703-465c4d8c2fae">     <Links>       <Link Rel="Delete" Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7/computeResources/25f485fd-06e3-4ee2-9703-465c4d8c2fae" Name="" />       <Link Rel="Up" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7?format=Entity" Name="ABC Company" />       <Link Rel="Up" Type="BackupServer" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982?format=Entity" Name="172.17.53.48" />     </Links>     <CloudHardwarePlanUid>urn:veeam:CloudHardwarePlan:91156f8d-8bd3-44af-bec3-b6ac2ea24288</CloudHardwarePlanUid>     <WanAcceleratorUid>urn:veeam:WanAccelerator:34ebeeb4-75d0-4e71-b315-fbc16eb2975f</WanAcceleratorUid>     <PlatformType>VMware</PlatformType>     <UseNetworkFailoverResources>true</UseNetworkFailoverResources>     <NetworkAppliance>       <Name>Cloud Appliance ABC Company(esx01)</Name>       <ProductionNetwork>VM Network</ProductionNetwork>       <ObtainIPAddressAutomatically>true</ObtainIPAddressAutomatically>       <ViDistributedSwitchUuid/>     </NetworkAppliance>     <ComputeResourceStats>       <MemoryUsageMb>8192</MemoryUsageMb>       <CPUCount>2</CPUCount>       <StorageResourceStats>         <StorageResourceStat>           <StorageName>Cloud Replicas</StorageName>           <StorageUsageGb>35</StorageUsageGb>           <StorageLimitGb>300</StorageLimitGb>         </StorageResourceStat>       </StorageResourceStats>     </ComputeResourceStats>   </CloudTenantComputeResource> </CloudTenantComputeResources> |

Page updated 2026-07-29

