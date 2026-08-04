---
title: "/nas/jobs/{ID}/includes"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/nas_jobs_id_includes.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /nas/jobs/{ID}/includes


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
| <NASObjects xmlns="http://www.veeam.com/ent/v1.0">   <NASObject Type="NasObject" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2/includes/6fefb504-856d-4c31-b767-76af5567c407">     <Links>       <Link Rel="Up" Type="Job" Href="https://srv12.tech.local:9398/api/nas/jobs/93dfbb3e-f420-45cf-addc-4ee9297113f2?format=Entity" Name="Shared Files Backup" />       <Link Rel="Related" Type="FileServer" Href="https://srv12.tech.local:9398/api/nas/fileServers/517be4c8-9c43-4e7c-9f59-4e368d3a8f3c?format=Entity" Name="\\srv12\share" />     </Links>     <HierarchyObjRef>urn:NasBackup:BackupServer:5735d1af-3aad-49ac-ac77-eab708ac1a37</HierarchyObjRef>     <ObjectInJobId>6fefb504-856d-4c31-b767-76af5567c407</ObjectInJobId>     <FileOrFolder>\\srv12\share</FileOrFolder>     <FileServerUid>urn:veeam:FileServer:517be4c8-9c43-4e7c-9f59-4e368d3a8f3c</FileServerUid>     <InclusionMask>       <Extension>\*.\*</Extension>     </InclusionMask>     <ExclusionMask>       <Extension>\\srv12\share\.snapshot</Extension>       <Extension>\\srv12\share\~snapshot</Extension>     </ExclusionMask>   </NASObject> </NASObjects> |

Page updated 2026-07-29

