---
title: "/cloud/tenants/{ID}/computeResources"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/tenants_id_computeresources.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

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
| <CloudTenantComputeResources xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
