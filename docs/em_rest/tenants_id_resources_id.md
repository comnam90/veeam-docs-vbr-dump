---
title: "/cloud/tenants/{ID}/resources/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/tenants_id_resources_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cloud/tenants/{ID}/resources/{ID}


Represents a storage quota assigned to the tenant account with the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}/resources/{ID} |

Related Resources

* [/backupServers](backupservers.md)
* [/cloud/tenants/{ID}/resources](tenants_id_resources.md)

Methods

The following methods are supported for the /cloud/tenants/{ID}/resources/{ID} resource:

* [GET /cloud/tenants/{ID}/resources/{ID}](get_tenants_id_resources_id.md)
* [DELETE /cloud/tenants/{ID}/resources/{ID}](delete_tenants_id_resources_id.md)

Resource Representation

The /cloud/tenants/{ID}/resources/{ID} resource has a resource representation of the following type.

|  |
| --- |
| <CloudTenantResource xmlns="http://www.veeam.com/ent/v1.0" Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89/resources/1c7c6cd7-0cd0-4e20-8d15-a94d23299a93" Id="1c7c6cd7-0cd0-4e20-8d15-a94d23299a93">   <Links>     <Link Rel="Delete" Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89/resources/1c7c6cd7-0cd0-4e20-8d15-a94d23299a93" Name="Cloud repository 3" />     <Link Rel="Up" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89?format=Entity" Name="ABC Company" />     <Link Rel="Up" Type="BackupServer" Href="https://localhost:9398/api/backupServers/8ea5406b-a6e9-42d9-bca5-44b6a5d94af1?format=Entity" Name="localhost" />   </Links>   <RepositoryQuota>     <DisplayName>Cloud repository 3</DisplayName>     <RepositoryUid>urn:veeam:Repository:82db96c3-445c-4a7e-9587-f2d523e839f4</RepositoryUid>     <Quota>1024</Quota>     <UsedQuota>0</UsedQuota>   </RepositoryQuota> </CloudTenantResource> |

Page updated 2026-07-29

