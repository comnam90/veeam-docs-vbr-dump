---
title: "/externalRepositories/{ID}/backups"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/externalrepositories_id_backups.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /externalRepositories/{ID}/backups


Represents a collection of all backups on backup servers connected to Veeam Backup Enterprise Manager filtered by an external repository with a specified ID as a target repository.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/externalRepositories/{ID}/backups |

Related Resources

[/backups/{ID}](backups_id.md)

Methods

The following methods are supported for the /externalRepositories/{ID}/backups resource:

[GET /backups](get_backups.md)

Resource Representation

The /externalRepositories/{ID}/backups resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:Backup:752b210a-0b35-4db8-b864-62c742aaa7b8" Name="AborWin2025r2\_i-0e274c7b93d261e28 Backup (AborCPM25\_07)" Href="http://local.host:9399/api/backups/752b210a-0b35-4db8-b864-62c742aaa7b8" Type="BackupReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/3e1e451a-4718-4475-836b-9547ccae6872" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/externalRepositories/06ff6c99-f457-4fd3-87da-4d00291d3eae" Name="External repository" Type="ExternalRepositoryReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/752b210a-0b35-4db8-b864-62c742aaa7b8?format=Entity" Name="AborWin2025r2\_i-0e274c7b93d261e28 Backup (AborCPM25\_07)" Type="Backup" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backups/752b210a-0b35-4db8-b864-62c742aaa7b8/restorePoints" Type="RestorePointReferenceList" Rel="Down"/>       <Link Href="http://local.host:9399/api/backups/50b010e6-4522-492a-a18e-d430c1bd4384" Name="Parent Backup" Type="BackupReference" Rel="Up"/>     </Links>   </Ref>   <Ref UID="urn:veeam:Backup:50b010e6-4522-492a-a18e-d430c1bd4384" Name="AborCPM25\_07" Href="http://local.host:9399/api/backups/50b010e6-4522-492a-a18e-d430c1bd4384" Type="BackupReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/3e1e451a-4718-4475-836b-9547ccae6872" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/externalRepositories/06ff6c99-f457-4fd3-87da-4d00291d3eae" Name="External repository" Type="ExternalRepositoryReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/50b010e6-4522-492a-a18e-d430c1bd4384?format=Entity" Name="AborCPM25\_07" Type="Backup" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backups/50b010e6-4522-492a-a18e-d430c1bd4384/childbackups" Type="BackupReferenceList" Rel="Up"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

