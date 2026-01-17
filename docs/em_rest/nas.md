---
title: "/nas"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/nas.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a collection of NAS backup resources. The /nas resource provides a set of links to the following resources:

* [NasJob](nas_jobs.md)
* [FileServer](nas_fileservers.md)
* [BackupJobSession](nas_backupsessions.md)

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/nas |

Related Resources

None.

Methods

The following methods are supported for the /nas resource:

[GET /nas](get_nas.md)

Resource Representation

The /nas resource has a resource representation of the following type:

|  |
| --- |
| <NASService xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
