---
title: "/cloud/tenants/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/tenants_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /cloud/tenants/{ID}


Represents a tenant account with the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/cloud/tenants](tenants.md)
* [/cloud/tenants/{ID}/resources](tenants_id_resources.md)
* [/cloud/tenants/{ID}/computeResources](tenants_id_computeresources.md)
* [/cloud/tenants/{ID}/vCloudComputeResources](cloud_tenants_id_vcloudcomputeresources.md)
* [/cloud/tenants/{ID}/subtenants](tenants_id_subtenants.md)
* [/cloud/tenants/{ID}/gatewayPools](tenants_id_gatewaypools.md)
* [/cloud/tenants/{ID}/freelicenseCounters](tenants_id_freelicensecounters.md)

Methods

The following methods are supported for the /cloud/tenants/{ID} resource:

* [GET /cloud/tenants/{ID}](get_tenants_id.md)
* [PUT /cloud/tenants/{ID}](put_tenants_id.md)
* [DELETE /cloud/tenants/{ID}](delete_tenants_id.md)

Resource Representation

The /cloud/tenants/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="CloudTenantReference" Href="https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7" Name="ABC Company" UID="urn:veeam:CloudTenant:b25f5f1d-a3c3-45ed-af23-9ef31a94dac7"> |

Entity resource representation:

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> <CloudTenant Href="http://local.host:9399/api/cloud/tenants/8c32c8b8-bc94-4677-acab-dd7b98a1df0e?format=Entity" Type="CloudTenant" Name="ABC Company" UID="urn:veeam:CloudTenant:8c32c8b8-bc94-4677-acab-dd7b98a1df0e" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Links>     <Link Href="http://local.host:9399/api/backupServers/a1134794-5a4f-446c-be5d-b433eaf1bc7e" Name="win10x64.tech.local" Type="BackupServerReference" Rel="Up"/>     <Link Href="http://local.host:9399/api/cloud/tenants/8c32c8b8-bc94-4677-acab-dd7b98a1df0e" Name="ABC Company" Type="CloudTenantReference" Rel="Alternate"/>     <Link Href="http://local.host:9399/api/cloud/tenants/8c32c8b8-bc94-4677-acab-dd7b98a1df0e" Name="ABC Company" Type="CloudTenantReference" Rel="Edit"/>     <Link Href="http://local.host:9399/api/cloud/tenants/8c32c8b8-bc94-4677-acab-dd7b98a1df0e/resources" Type="CloudTenantResourceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/tenants/8c32c8b8-bc94-4677-acab-dd7b98a1df0e/resources" Type="CloudTenantResource" Rel="Create"/>     <Link Href="http://local.host:9399/api/cloud/tenants/8c32c8b8-bc94-4677-acab-dd7b98a1df0e" Rel="Delete"/>     <Link Href="http://local.host:9399/api/cloud/tenants/8c32c8b8-bc94-4677-acab-dd7b98a1df0e/computeResources" Type="CloudTenantComputeResourceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/tenants/8c32c8b8-bc94-4677-acab-dd7b98a1df0e/computeResources" Type="CloudTenantComputeResource" Rel="Create"/>     <Link Href="http://local.host:9399/api/cloud/tenants/8c32c8b8-bc94-4677-acab-dd7b98a1df0e/subtenants" Type="CloudSubtenantList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/tenants/8c32c8b8-bc94-4677-acab-dd7b98a1df0e/subtenants" Type="CloudSubtenant" Rel="Create"/>     <Link Href="http://local.host:9399/api/cloud/tenants/8c32c8b8-bc94-4677-acab-dd7b98a1df0e/freelicenseCounters" Name="FreeLicenseCounters" Type="FreeLicenseCounters" Rel="Related"/>   </Links>   <Password/>   <Description>Tenant account for ABC Company</Description>   <Enabled>true</Enabled>   <LeaseOptions Enabled="false"/>   <Resources>     <CloudTenantResource Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7/resources/2fcc7f11-2a33-448d-a242-ba8f0618c97b" Id="2fcc7f11-2a33-448d-a242-ba8f0618c97b">       <RepositoryQuota>         <DisplayName>Cloud Vol 01</DisplayName>         <RepositoryUid>urn:veeam:Repository:a0f35f34-8d58-4470-b52d-071e1417732a</RepositoryUid>         <WanAcceleratorUid>urn:veeam:WanAccelerator:34ebeeb4-75d0-4e71-b315-fbc16eb2975f</WanAcceleratorUid>         <Quota>307200</Quota>       </RepositoryQuota>     </CloudTenantResource>     <CloudTenantResource Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7/resources/8c6aa6b6-4668-4f81-9729-60c56b9b300b" Id="8c6aa6b6-4668-4f81-9729-60c56b9b300b">       <RepositoryQuota>         <DisplayName>Cloud Repository 2</DisplayName>         <RepositoryUid>urn:veeam:Repository:0a9c15f5-bc17-4848-a14b-b2ec3f9919ea</RepositoryUid>         <Quota>102400</Quota>       </RepositoryQuota>     </CloudTenantResource>   </Resources>   <LastResult>Success</LastResult>   <LastActive>1753-01-01T00:00:00Z</LastActive>   <ComputeResources>     <CloudTenantComputeResource Type="CloudTenantComputeResource" Href="https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7/computeResources/25f485fd-06e3-4ee2-9703-465c4d8c2fae" Id="25f485fd-06e3-4ee2-9703-465c4d8c2fae">       <CloudHardwarePlanUid>urn:veeam:CloudHardwarePlan:91156f8d-8bd3-44af-bec3-b6ac2ea24288</CloudHardwarePlanUid>       <WanAcceleratorUid>urn:veeam:WanAccelerator:34ebeeb4-75d0-4e71-b315-fbc16eb2975f</WanAcceleratorUid>       <PlatformType>VMware</PlatformType>       <UseNetworkFailoverResources>true</UseNetworkFailoverResources>       <NetworkAppliance>         <Name>Cloud Appliance ABC Company(esx01)</Name>         <ProductionNetwork>VM Network</ProductionNetwork>         <ObtainIPAddressAutomatically>true</ObtainIPAddressAutomatically>         <ViDistributedSwitchUuid />         <ProductionNetworkUnderDvs>false</ProductionNetworkUnderDvs>       </NetworkAppliance>       <ComputeResourceStats>         <MemoryUsageMb>8192</MemoryUsageMb>         <CPUCount>2</CPUCount>         <StorageResourceStats>           <StorageResourceStat>             <StorageName>Cloud Replicas</StorageName>             <StorageUsageGb>35</StorageUsageGb>             <StorageLimitGb>300</StorageLimitGb>           </StorageResourceStat>         </StorageResourceStats>       </ComputeResourceStats>     </CloudTenantComputeResource>   </ComputeResources>   <ThrottlingEnabled>false</ThrottlingEnabled>   <ThrottlingSpeedLimit>1</ThrottlingSpeedLimit>   <ThrottlingSpeedUnit>MBps</ThrottlingSpeedUnit>   <PublicIpCount>0</PublicIpCount>   <BackupCount>0</BackupCount>   <ReplicaCount>0</ReplicaCount>   <MaxConcurrentTasks>1</MaxConcurrentTasks>   <WorkStationBackupCount>0</WorkStationBackupCount>   <ServerBackupCount>0</ServerBackupCount>   <BackupProtectionEnabled>false</BackupProtectionEnabled>   <BackupProtectionPeriod>1</BackupProtectionPeriod>   <TenantType>     <StandaloneTenant>       <TenantCredentials>         <Username>ABC Company</Username>       </TenantCredentials>     </StandaloneTenant>   </TenantType> </CloudTenant> |


