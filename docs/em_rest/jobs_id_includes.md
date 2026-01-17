---
title: "/jobs/{ID}/includes"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/jobs_id_includes.html"
last_updated: "9/1/2023"
product_version: "13.0.1.1071"
---


In this article

Represents a collection of VMs and VM containers processed by the job with the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/jobs/{ID}/includes |

Related Resources

* [/jobs/{ID}](jobs_id.md)
* [/jobs/{ID}/includes/{ID}](jobs_id_includes_id.md)

Methods

The following methods are supported for the /jobs/{ID}/includes resource:

* [GET /jobs/{ID}/includes](get_jobs_id_includes.md)
* [POST /jobs/{ID}/includes](post_jobs_id_includes.md)

Resource Representation

The /jobs/{ID}/includes resource has a resource representation of the following type:

|  |
| --- |
| <ObjectsInJob xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 9/1/2023

Page content applies to build 13.0.1.1071
