---
title: "/backups/{ID}/restorePoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backups_id_restorepoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /backups/{ID}/restorePoints


Represents a collection of restore points of [Standard and ChildBackup](get_backups_id.md#BackupType) backups having the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backups/{ID}/restorePoints |

Related Resources

[/backups/{ID}](backups_id.md)

Methods

The following methods are supported for the /backups/{ID}/restorePoints resource:

[GET /backups/{ID}/restorePoints](get_backups_id_restorepoints.md)

Resource Representation

The /backups/{ID}/restorePoints resource has a resource representation of the following type:

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:RestorePoint:ec940768-5428-41af-b9b6-afad2aefe9d6" Name="Jan 17 2025  5:21PM" Href="https://localhost:9398/api/restorePoints/ec940768-5428-41af-b9b6-afad2aefe9d6" Type="RestorePointReference">     <Links>       <Link Href="https://localhost:9398/api/backupServers/4ad6fa62-9164-4ea0-87c8-1e2d071d60de" Name="srv30" Type="BackupServerReference" Rel="Up"/>       <Link Href="https://localhost:9398/api/backups/a24cf6da-569e-45f8-8c39-544bfd2c22d6" Name="WindowsFileLevelRestoreFromCatalog" Type="BackupReference" Rel="Up"/>       <Link Href="https://localhost:9398/api/restorePoints/ec940768-5428-41af-b9b6-afad2aefe9d6?format=Entity" Name="Jan 17 2025  5:21PM" Type="RestorePoint" Rel="Alternate"/>       <Link Href="https://localhost:9398/api/restorePoints/ec940768-5428-41af-b9b6-afad2aefe9d6/vmRestorePoints" Type="VmRestorePointReferenceList" Rel="Down"/>       <Link Href="https://localhost:9398/api/restorePoints/ec940768-5428-41af-b9b6-afad2aefe9d6/backupFiles" Type="RestorePointReferenceList" Rel="Related"/>     </Links>   </Ref>   ... </EntityReferences> |

Page updated 2026-07-29

