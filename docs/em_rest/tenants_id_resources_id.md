---
title: "tenants_id_resources_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/tenants_id_resources_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

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
| <CloudTenantResource xmlns="http://www.veeam.com/ent/v1.0" Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89/resources/1c7c6cd7-0cd0-4e20-8d15-a94d23299a93" Id="1c7c6cd7-0cd0-4e20-8d15-a94d23299a93"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
