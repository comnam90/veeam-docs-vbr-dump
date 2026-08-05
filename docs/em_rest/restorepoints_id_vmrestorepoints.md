---
title: "/restorePoints/{ID}/vmRestorePoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/restorepoints_id_vmrestorepoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /restorePoints/{ID}/vmRestorePoints


Represents a collection of restore points for separate VMs created for a backup restore point with the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/restorePoints/{ID}/vmRestorePoints |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/restorePoints/{ID}](restorepoints_id.md)
* [/backupFiles/{ID}](backupfiles_id.md)
* [/vmRestorePoints/{ID}](vmrestorepoints_id.md)

Methods

The following methods are supported for the /restorePoints/{ID}/vmRestorePoints resource:

[GET /restorePoints/{ID}/vmRestorePoints](get_restorepoints_id_vmrestorepoints.md)

Resource Representation

The /restorePoints/{ID}/vmRestorePoints resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/5acac742-ee17-4080-8e89-a6ea67adfcf3" Name="oracle03@2025-10-06 13:59:50" UID="urn:veeam:VmRestorePoint:5acac742-ee17-4080-8e89-a6ea67adfcf3">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/00fd67d9-2b4c-4c56-8a95-0b3dbec7ae43" Name="172.17.53.1" />       <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/dc216c04-2e34-478e-8b9b-49a3397ef6f8" Name="Oct  6 2025  1:59PM" />       <Link Rel="Up" Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/e86f61f9-4220-4f55-820b-e41a38abce90" Name="Oracle BackupD2025-10-06T165918.vib" />       <Link Rel="Alternate" Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/5acac742-ee17-4080-8e89-a6ea67adfcf3?format=Entity" Name="oracle03@2025-10-06 13:59:50" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

