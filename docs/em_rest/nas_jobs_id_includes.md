---
title: "nas_jobs_id_includes"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/nas_jobs_id_includes.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a collection of files and folders processed by the file share backup job with the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/nas/jobs/{ID}/includes |

Related Resources

* [/nas/jobs/{ID}](nas_jobs_id.md)
* [/nas/jobs/{ID}/includes/{ID}](nas_jobs_id_includes_id.md)
* [/nas/fileServers/{ID}](nas_fileservers_id.md)

Methods

The following methods are supported for the /nas/jobs/{ID}/includes resource:

[GET /nas/jobs/{ID}/includes](get_nas_jobs_id_includes.md)

Resource Representation

The /nas/jobs/{ID}/includes resource has a resource representation of the following type:

|  |
| --- |
| <NASObjects xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
