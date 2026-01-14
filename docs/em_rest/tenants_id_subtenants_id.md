---
title: "tenants_id_subtenants_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/tenants_id_subtenants_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

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
| <CloudSubtenant xmlns="http://www.veeam.com/ent/v1.0" Type="CloudSubtenant" Href="https://localhost:9398/api/cloud/tenants/28ddf9b9-12fa-431a-a34c-a327f05c3920/subtenants/0eb0c130-d91a-4e05-9403-ac2ded0fc1ea" Id="0eb0c130-d91a-4e05-9403-ac2ded0fc1ea"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
