---
title: "jobs_id_includes_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/jobs_id_includes_id.html"
last_updated: "9/1/2023"
product_version: "13.0.1.1071"
---


In this article

Represents a VM or a VM container having the specified ID and processed by the job with the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/jobs/{ID}/includes/{ID} |

Related Resources

* [/jobs/{ID}](jobs_id.md)
* [/jobs/{ID}/includes](jobs_id_includes.md)

Methods

The following methods are supported for the /jobs/{ID}/includes/{ID} resource:

* [GET /jobs/{ID}/includes/{ID}](get_jobs_id_includes_id.md)
* [DELETE /jobs/{ID}/includes/{ID}](delete_jobs_id_includes_id.md)

Resource Representation

The /jobs/{ID}/includes/{ID} resource has a resource representation of the following type:

|  |
| --- |
| <ObjectInJob xmlns="http://www.veeam.com/ent/v1.0" Type="ObjectInJob" Href="https://localhost:9398/api/jobs/da4a15c2-04e7-4135-b876-577249d3d720/includes/83071dc0-44f2-49b6-b431-1cb79ed66639"> |

Page updated 9/1/2023

Page content applies to build 13.0.1.1071
