---
title: "/cloud/tenants"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/tenants.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cloud/tenants


Represents a collection of tenant accounts created on all backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/tenants |

Related Resources

[/cloud/tenants/{ID}](tenants_id.md)

Methods

The following methods are supported for the /cloud/tenants resource:

* [GET /cloud/tenants](get_tenants.md)
* [POST /cloud/tenants](post_tenants.md)

Resource Representation

The /cloud/tenants resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CloudTenantReference" Href="https://localhost:9398/api/cloud/tenants/b3ed42c9-3022-4958-864f-3df32e8436f9" Name="UCM Company" UID="urn:veeam:CloudTenant:b3ed42c9-3022-4958-864f-3df32e8436f9">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8ea5406b-a6e9-42d9-bca5-44b6a5d94af1" Name="localhost" />       <Link Rel="Alternate" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/b3ed42c9-3022-4958-864f-3df32e8436f9?format=Entity" Name="UCM Company" />     </Links>   </Ref>   <Ref Type="CloudTenantReference" Href="https://localhost:9398/api/cloud/tenants/9e76e394-9dfe-4089-bc0d-569c5376ae86" Name="Applied Systems Company" UID="urn:veeam:CloudTenant:9e76e394-9dfe-4089-bc0d-569c5376ae86">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8ea5406b-a6e9-42d9-bca5-44b6a5d94af1" Name="localhost" />       <Link Rel="Alternate" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/9e76e394-9dfe-4089-bc0d-569c5376ae86?format=Entity" Name="Applied Systems Company" />     </Links>   </Ref>   <Ref Type="CloudTenantReference" Href="https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89" Name="ABC Company" UID="urn:veeam:CloudTenant:4f90635a-7ecc-49fe-beb6-60b37eb4bd89">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8ea5406b-a6e9-42d9-bca5-44b6a5d94af1" Name="localhost" />       <Link Rel="Alternate" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89?format=Entity" Name="ABC Company" />     </Links>   </Ref>   <Ref Type="CloudTenantReference" Href="https://localhost:9398/api/cloud/tenants/20602b2b-d55b-436c-9010-b4c7046c294a" Name="Tri-M Company" UID="urn:veeam:CloudTenant:20602b2b-d55b-436c-9010-b4c7046c294a">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8ea5406b-a6e9-42d9-bca5-44b6a5d94af1" Name="localhost" />       <Link Rel="Alternate" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/20602b2b-d55b-436c-9010-b4c7046c294a?format=Entity" Name="Tri-M Company" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

