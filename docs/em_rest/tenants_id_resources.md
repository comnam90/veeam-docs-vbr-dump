---
title: "/cloud/tenants/{ID}/resources"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/tenants_id_resources.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cloud/tenants/{ID}/resources


Represents a collection of storage quotas assigned to the tenant account with the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}/resources |

Related Resources

* [/backupServers](backupservers.md)
* [/cloud/tenants/{ID}](tenants_id.md)

Methods

The following methods are supported for the /cloud/tenants/{ID}/resources resource:

* [GET /cloud/tenants/{ID}/resources](get_tenants_id_resources.md)
* [POST /cloud/tenants/{ID}/resources](post_tenants_id_resources.md)

Resource Representation

The /cloud/tenants/{ID}/resources resource has a resource representation of the following type.

|  |
| --- |
| <CloudTenantResources xmlns="http://www.veeam.com/ent/v1.0">   <CloudTenantResource Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89/resources/7401a50c-4dba-4fc9-81a8-2b33afdb2e39" Id="7401a50c-4dba-4fc9-81a8-2b33afdb2e39">     <Links>       <Link Rel="Delete" Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89/resources/7401a50c-4dba-4fc9-81a8-2b33afdb2e39" Name="Cloud repository 2" />       <Link Rel="Up" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89?format=Entity" Name="ABC Company" />       <Link Rel="Up" Type="BackupServer" Href="https://localhost:9398/api/backupServers/8ea5406b-a6e9-42d9-bca5-44b6a5d94af1?format=Entity" Name="localhost" />     </Links>     <RepositoryQuota>       <DisplayName>Cloud repository 2</DisplayName>       <RepositoryUid>urn:veeam:Repository:bcf56d1e-acc8-4099-8708-00f62930b1ac</RepositoryUid>       <Quota>10240</Quota>       <UsedQuota>0</UsedQuota>     </RepositoryQuota>   </CloudTenantResource>   <CloudTenantResource Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89/resources/725fad57-2606-4903-98ba-b435f303670e" Id="725fad57-2606-4903-98ba-b435f303670e">     <Links>       <Link Rel="Delete" Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89/resources/725fad57-2606-4903-98ba-b435f303670e" Name="Cloud repository 1" />       <Link Rel="Up" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89?format=Entity" Name="ABC Company" />       <Link Rel="Up" Type="BackupServer" Href="https://localhost:9398/api/backupServers/8ea5406b-a6e9-42d9-bca5-44b6a5d94af1?format=Entity" Name="localhost" />     </Links>     <RepositoryQuota>       <DisplayName>Cloud repository 1</DisplayName>       <RepositoryUid>urn:veeam:Repository:82db96c3-445c-4a7e-9587-f2d523e839f4</RepositoryUid>       <Quota>10240</Quota>       <UsedQuota>0</UsedQuota>     </RepositoryQuota>   </CloudTenantResource> </CloudTenantResources> |

Page updated 2026-07-29

