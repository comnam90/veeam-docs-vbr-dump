---
title: "repositories_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/repositories_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a backup repository having the specified ID. The backup repository is created on the backup server connected to Veeam Backup Enterprise Manager.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/repositories/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/repositories/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/backups](backups.md)
* [/replicas](replicas.md)

Methods

The following methods are supported for the /repositories/{ID} resource:

[GET /repositories/{ID}](get_repositories_id.md)

Resource Representation

The /repositories/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="RepositoryReference" Href="https://localhost:9398/api/repositories/bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6" Name="Backup Volume 01" UID="urn:veeam:Repository:bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6"> |

Entity resource representation:

|  |
| --- |
| <Repository xmlns="http://www.veeam.com/ent/v1.0" Type="Repository" Href="https://localhost:9398/api/repositories/bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6?format=Entity" Name="Backup Volume 01" UID="urn:veeam:Repository:bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />     <Link Rel="Alternate" Type="RepositoryReference" Href="https://localhost:9398/api/repositories/bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6" Name="Backup Volume 01" />     <Link Rel="Down" Type="BackupReferenceList" Href="https://localhost:9398/api/repositories/bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6/backups" />     <Link Rel="Down" Type="ReplicaReferenceList" Href="https://localhost:9398/api/repositories/bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6/replicas" />   </Links>   <Capacity>1079639011328</Capacity>   <FreeSpace>881812750336</FreeSpace>   <Kind>WindowsLocal</Kind> </Repository> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
