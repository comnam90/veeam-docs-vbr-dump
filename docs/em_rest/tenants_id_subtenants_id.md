---
title: "/cloud/tenants/{ID}/subtenants/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/tenants_id_subtenants_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cloud/tenants/{ID}/subtenants/{ID}


Represents a subtenant account created for the tenant account with the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}/subtenants/{ID} |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/cloud/tenants/{ID}](tenants_id.md)
* [/cloud/tenants/{ID}/subtenants](tenants_id_subtenants.md)

Methods

The following methods are supported for the /cloud/tenants/{ID}/subtenants/{ID} resource:

* [GET /cloud/tenants/{ID}/subtenants/{ID}](get_tenants_id_subtenants_id.md)
* [PUT /cloud/tenants/{ID}/subtenants/{ID}](put_tenants_id_subtenants_id.md)
* [DELETE /cloud/tenants/{ID}/subtenants/{ID}](delete_tenants_id_subtenants_id.md)

Resource Representation

The /cloud/tenants/{ID}/subtenants/{ID} resource has a resource representation of the following type.

|  |
| --- |
| <CloudSubtenant xmlns="http://www.veeam.com/ent/v1.0" Type="CloudSubtenant" Href="https://localhost:9398/api/cloud/tenants/28ddf9b9-12fa-431a-a34c-a327f05c3920/subtenants/0eb0c130-d91a-4e05-9403-ac2ded0fc1ea" Id="0eb0c130-d91a-4e05-9403-ac2ded0fc1ea">   <Links>     <Link Rel="Edit" Type="CloudSubtenant" Href="https://localhost:9398/api/cloud/tenants/28ddf9b9-12fa-431a-a34c-a327f05c3920/subtenants/0eb0c130-d91a-4e05-9403-ac2ded0fc1ea" Name="ABC Company User 01" />     <Link Rel="Delete" Href="https://localhost:9398/api/cloud/tenants/28ddf9b9-12fa-431a-a34c-a327f05c3920/subtenants/0eb0c130-d91a-4e05-9403-ac2ded0fc1ea" />     <Link Rel="Up" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/28ddf9b9-12fa-431a-a34c-a327f05c3920?format=Entity" Name="ABC Company" />     <Link Rel="Up" Type="BackupServer" Href="https://localhost:9398/api/backupServers/1cf4ea89-89d9-4b4e-a285-71bd8c705222?format=Entity" Name="172.17.53.2" />   </Links>   <Name>ABC Company User 01</Name>   <Description>ABC Company PC User</Description>   <Password />   <Enabled>true</Enabled>   <RepositoryQuota Unlimited="true">     <DisplayName>Cloud Vol User 01</DisplayName>     <TenantResourceId>11c59670-23df-448c-a4b3-74c42669633e</TenantResourceId>     <QuotaMb>20480</QuotaMb>     <UsedQuotaMb>0</UsedQuotaMb>   </RepositoryQuota> </CloudSubtenant> |

Page updated 2026-07-29

