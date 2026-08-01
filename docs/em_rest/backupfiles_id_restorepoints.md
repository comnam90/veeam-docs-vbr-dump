---
title: "/backupFiles/{ID}/restorePoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backupfiles_id_restorepoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /backupFiles/{ID}/restorePoints


Represents a collection of restore points for a backup file with the specified ID. The backup file was created on or imported to a backup server connected to Veeam Backup Enterprise Manager.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backupFiles/{ID}/restorePoints |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/backups/{ID}](backups_id.md)
* [/restorePoints/{ID}/vmRestorePoints](restorepoints_id_vmrestorepoints.md)
* [/restorePoints/{ID}/vAppRestorePoints](restorepoints_id_vapprestorepoints.md)
* [/restorePoints/{ID}/backupFiles](restorepoints_id_backupfiles.md)

Methods

The following methods are supported for the /backupFiles/{ID}/restorePoints resource:

[GET /backupFiles/{ID}/restorePoints](get_backupfiles_id_restorepoints.md)

Resource Representation

The /backupFiles/{ID}/restorePoints resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/33732b87-1074-4883-bc3c-25931fbea4ed" Name="Sep 19 2025  9:00PM" UID="urn:veeam:RestorePoint:33732b87-1074-4883-bc3c-25931fbea4ed">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/99f01406-ecdc-428f-ae09-a13de244140a" Name="172.17.53.1" />       <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/80672bda-76a8-408b-947f-afd0ff67fba6" Name="Webserver Backup Copy" />       <Link Rel="Alternate" Type="RestorePoint" Href="https://localhost:9398/api/restorePoints/33732b87-1074-4883-bc3c-25931fbea4ed?format=Entity" Name="Sep 19 2025  9:00PM" />       <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/33732b87-1074-4883-bc3c-25931fbea4ed/vmRestorePoints" />       <Link Rel="Down" Type="VAppRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/33732b87-1074-4883-bc3c-25931fbea4ed/vAppRestorePoints" />       <Link Rel="Related" Type="RestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/33732b87-1074-4883-bc3c-25931fbea4ed/backupFiles" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

