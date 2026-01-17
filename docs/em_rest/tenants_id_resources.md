---
title: "/cloud/tenants/{ID}/resources"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/tenants_id_resources.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

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
| <CloudTenantResources xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
