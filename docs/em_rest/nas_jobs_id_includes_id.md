---
title: "/nas/jobs/{ID}/includes/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/nas_jobs_id_includes_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /nas/jobs/{ID}/includes/{ID}


Represents a file or folder having the specified ID and processed by the file share backup job with the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/nas/jobs/{ID}/includes/{ID} |

Related Resources

* [/nas/jobs/{ID}](nas_jobs_id.md)
* [/nas/fileServers/{ID}](nas_fileservers_id.md)

Methods

The following methods are supported for the /nas/jobs/{ID}/includes/{ID} resource:

[GET /jobs/{ID}/includes/{ID}](get_jobs_id_includes_id.md)

Resource Representation

The /nas/jobs/{ID}/includes/{ID} resource has a resource representation of the following type:

|  |
| --- |
| <NASObject xmlns="http://www.veeam.com/ent/v1.0" Type="NasObject" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2/includes/6fefb504-856d-4c31-b767-76af5567c407"> |


