---
title: "jobs_id_linked_jobs"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/jobs_id_linked_jobs.html"
last_updated: "8/20/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a collection of backup jobs linked to the backup copy job with the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/jobs/{ID}/includes/{ID} |

Related Resources

[/jobs/{ID}](jobs_id.md)

Methods

The following methods are supported for the /jobs/{ID}/includes/{ID} resource:

* [GET /jobs/{ID}/linkedJobs](get_jobs_id_linked_jobs.md)
* [POST /jobs/{ID}/linkedJobs](post_jobs_id_linked_jobs.md)
* [DELETE /jobs/{ID}/linkedJobs/{ID}](delete_jobs_id_linked_jobs.md)

Resource Representation

The /jobs/{ID}/linkedJobs resource has a resource representation of the following type:

|  |
| --- |
| <<LinkedJobResourceObjects xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 8/20/2025

Page content applies to build 13.0.1.1071
