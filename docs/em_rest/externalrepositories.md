---
title: "/externalRepositories"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/externalrepositories.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /externalRepositories


Represents a collection of all external backup repositories on backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/externalRepositories |

Related Resources

[/externalRepositories/{ID}](externalrepositories_id.md)

Methods

The following methods are supported for the /externalRepositories resource:

[GET /externalRepositories](get_externalrepositories.md)

Resource Representation

The /externalRepositories resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:ExternalRepository:06ff6c99-f457-4fd3-87da-4d00291d3eae" Name="External repository" Href="http://local.host:9399/api/externalRepositories/06ff6c99-f457-4fd3-87da-4d00291d3eae" Type="ExternalRepositoryReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/3e1e451a-4718-4475-836b-9547ccae6872" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/externalRepositories/06ff6c99-f457-4fd3-87da-4d00291d3eae?format=Entity" Name="External repository" Type="ExternalRepository" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/externalRepositories/06ff6c99-f457-4fd3-87da-4d00291d3eae/backups" Type="BackupReferenceList" Rel="Down"/>     </Links>   </Ref>   ... </EntityReferences> |

Page updated 2026-07-29

