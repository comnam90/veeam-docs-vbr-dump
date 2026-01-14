---
title: "externalrepositories_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/externalrepositories_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents an external backup repository having the specified ID. The external backup repository is added to the backup server connected to Veeam Backup Enterprise Manager.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/externalRepositories/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/externalRepositories/{ID}?format=Entity |

Related Resources

* [/externalRepositories](externalrepositories.md)
* [/backupServers/{ID}](backupservers_id.md)
* [/backups](backups.md)
* [/replicas](replicas.md)

Methods

The following methods are supported for the /externalRepositories/{ID} resource:

[GET /externalRepositories/{ID}](get_externalrepositories_id.md)

Resource Representation

The /externalRepositories/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef UID="urn:veeam:ExternalRepository:06ff6c99-f457-4fd3-87da-4d00291d3eae" Name="External repository" Href="http://local.host:9399/api/externalRepositories/06ff6c99-f457-4fd3-87da-4d00291d3eae" Type="ExternalRepositoryReference" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> |

Entity resource representation:

|  |
| --- |
| <ExternalRepository Href="http://local.host:9399/api/externalRepositories/06ff6c99-f457-4fd3-87da-4d00291d3eae?format=Entity" Type="ExternalRepository" Name="External repository" UID="urn:veeam:ExternalRepository:06ff6c99-f457-4fd3-87da-4d00291d3eae" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Links>     <Link Href="http://local.host:9399/api/backupServers/3e1e451a-4718-4475-836b-9547ccae6872" Name="local.host" Type="BackupServerReference" Rel="Up"/>     <Link Href="http://local.host:9399/api/externalRepositories/06ff6c99-f457-4fd3-87da-4d00291d3eae" Name="External repository" Type="ExternalRepositoryReference" Rel="Alternate"/>     <Link Href="http://local.host:9399/api/externalRepositories/06ff6c99-f457-4fd3-87da-4d00291d3eae/backups" Type="BackupReferenceList" Rel="Down"/>   </Links>   <RepositoryType>AmazonS3External</RepositoryType>   <Path>amazonS3://amazon/repository</Path>   <UsedSpace>10037476573</UsedSpace>   <Description>Created by srv02\admin.</Description> </ExternalRepository> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
