---
title: "/restorePoints/{ID}/backupFiles"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/restorepoints_id_backupfiles.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /restorePoints/{ID}/backupFiles


Represents a collection of backup files created for a restore point with the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/restorePoints/{ID}/backupFiles |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/backups/{ID}](backups_id.md)
* [/backupFiles/{ID}](backupfiles_id.md)
* [/backupFiles/{ID}/restorePoints](backupfiles_id_restorepoints.md)
* [/backupFiles/{ID}/vmRestorePoints](backupfiles_id_vmrestorepoints.md)

Methods

The following methods are supported for the /restorePoints/{ID}/backupFiles resource:

[GET /restorePoints/{ID}/backupFiles](get_restorepoints_id_backupfiles.md)

Resource Representation

The /restorePoints/{ID}/backupFiles resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/e86f61f9-4220-4f55-820b-e41a38abce90" Name="Oracle BackupD2025-10-06T165918.vib" UID="urn:veeam:BackupFile:e86f61f9-4220-4f55-820b-e41a38abce90">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/00fd67d9-2b4c-4c56-8a95-0b3dbec7ae43" Name="172.17.53.1" />       <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/61270417-d856-463f-abc4-b5ae70a2e1ab" Name="Oracle Backup" />       <Link Rel="Alternate" Type="BackupFile" Href="https://localhost:9398/api/backupFiles/e86f61f9-4220-4f55-820b-e41a38abce90?format=Entity" Name="Oracle BackupD2025-10-06T165918.vib" />       <Link Rel="Related" Type="BackupFileReferenceList" Href="https://localhost:9398/api/backupFiles/e86f61f9-4220-4f55-820b-e41a38abce90/restorePoints" />       <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/backupFiles/e86f61f9-4220-4f55-820b-e41a38abce90/vmRestorePoints" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

