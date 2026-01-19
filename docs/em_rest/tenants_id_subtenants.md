---
title: "/cloud/tenants/{ID}/subtenants"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/tenants_id_subtenants.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /cloud/tenants/{ID}/subtenants


Represents a collection of subtenant accounts created for the tenant account with the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}/subtenants |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/cloud/tenants/{ID}](tenants_id.md)
* [/cloud/tenants/{ID}/subtenants/{ID}](tenants_id_subtenants_id.md)

Methods

The following methods are supported for the /cloud/tenants/{ID}/subtenants resource:

* [GET /cloud/tenants/{ID}/subtenants](get_tenants_id_subtenants.md)
* [POST /cloud/tenants/{ID}/subtenants](post_tenants_id_subtenants.md)

Resource Representation

The /cloud/tenants/{ID}/subtenants resource has a resource representation of the following type.

|  |
| --- |
| <CloudSubtenants xmlns="http://www.veeam.com/ent/v1.0"> |


