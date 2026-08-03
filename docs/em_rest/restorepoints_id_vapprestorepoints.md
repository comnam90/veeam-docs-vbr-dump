---
title: "/restorePoints/{ID}/vAppRestorePoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/restorepoints_id_vapprestorepoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /restorePoints/{ID}/vAppRestorePoints


Represents a collection of vApp restore points created for a backup restore point with the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/restorePoints/{ID}/vAppRestorePoints |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/restorePoints/{ID}](restorepoints_id.md)
* [/vAppRestorePoints/{ID}](vapprestorepoints_id.md)

Methods

The following methods are supported for the /restorePoints/{ID}/vAppRestorePoints resource:

[GET /restorePoints/{ID}/vAppRestorePoints](get_restorepoints_id_vapprestorepoints.md)

Resource Representation

The /restorePoints/{ID}/vAppRestorePoints resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="VAppRestorePointReference" Href="https://localhost:9398/api/vAppRestorePoints/5edbd79d-273a-4688-bca8-228c4a1586d7" Name="vApp\_1@2025-10-25 14:50:08" UID="urn:veeam:VAppRestorePoint:5edbd79d-273a-4688-bca8-228c4a1586d7">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/00fd67d9-2b4c-4c56-8a95-0b3dbec7ae43" Name="172.17.53.1" />       <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/aaf85ac9-f53c-4dfa-9837-024ad87ef4b6" Name="Oct 25 2025  2:49PM" />       <Link Rel="Alternate" Type="VAppRestorePoint" Href="https://localhost:9398/api/vAppRestorePoints/5edbd79d-273a-4688-bca8-228c4a1586d7?format=Entity" Name="vApp\_1@2025-10-25 14:50:08" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

