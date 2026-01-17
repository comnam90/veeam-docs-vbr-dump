---
title: "/cloud/tenants/{ID}/computeResources/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/tenants_id_computeresources_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a hardware plan with the specified ID to which the tenant account with the specified ID is subscribed.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}/computeResources/{ID} |

Related Resources

* [/cloud/tenants/{ID}](tenants_id.md)
* [/cloud/tenants/{ID}/computeResources](tenants_id_computeresources.md)

Methods

The following methods are supported for the /cloud/tenants/{ID}/computeResources/{ID} resource:

* [GET /cloud/tenants/{ID}/computeResources/{ID}](get_tenants_id_computeresources_id.md)
* [DELETE /cloud/tenants/{ID}/computeResources/{ID}](delete_tenants_id_computeresources_id.md)

Resource Representation

The /cloud/tenants/{ID}/computeResources/{ID} resource has a resource representation of the following type.

|  |
| --- |
| <CloudTenantComputeResource xmlns="http://www.veeam.com/ent/v1.0" Type="CloudTenantComputeResource" Href="https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7/computeResources/25f485fd-06e3-4ee2-9703-465c4d8c2fae" Id="25f485fd-06e3-4ee2-9703-465c4d8c2fae"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
