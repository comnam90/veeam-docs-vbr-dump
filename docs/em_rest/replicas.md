---
title: "/replicas"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/replicas.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /replicas


Represents a collection of all replicas created on backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Note |
| The /replicas resource represents only regular VM replicas created on a backup server managed by Veeam Backup Enterprise Manager. Cloud replicas created by tenants whose accounts are created on a backup server appear in the /cloud/replicas resource representation. |

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/replicas |

Related Resources

[/replicas/{ID}](replicas_id.md)

Methods

The following methods are supported for the /replicas resource:

[GET /replicas](get_replicas.md)

Resource Representation

The /replicas resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |


