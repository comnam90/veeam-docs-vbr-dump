---
title: "/backups/{ID}/childbackups"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backups_id_childbackups.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /backups/{ID}/childbackups


Represents a collection of all [ChildBackup](get_backups_id.md#BackupType) resources of a [ParentBackup](get_backups_id.md#BackupType) backup type having the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backups/{ID}/childbackups |

Related Resources

[/backups/{ID}](backups_id.md)

Methods

The following methods are supported for the /backups/{ID}/childbackups resource:

[GET /backups/{ID}/childbackups](get_backups_id_childbackups.md)

Resource Representation

The /backups/{ID}/childbackups resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:Backup:da68ee31-a90b-44b7-bfab-a1eb49b9d352" Name="VM number 0 Backup (Simple backup)" Href="http://local.host:9399/api/backups/da68ee31-a90b-44b7-bfab-a1eb49b9d352" Type="BackupReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/repositories/b8832f03-2c9e-4222-8d0b-e43e0c912f93" Name="Scale-out Backup Repository 2" Type="RepositoryReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/da68ee31-a90b-44b7-bfab-a1eb49b9d352?format=Entity" Name="VM number 0 Backup (Simple backup)" Type="Backup" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backups/da68ee31-a90b-44b7-bfab-a1eb49b9d352/restorePoints" Type="RestorePointReferenceList" Rel="Down"/>       <Link Href="http://local.host:9399/api/backups/7b6a400c-452c-41d1-bb81-ea682e89492d" Name="Parent Backup" Type="BackupReference" Rel="Up"/>     </Links>   </Ref>   ... </EntityReferences> |

Page updated 2026-07-29

