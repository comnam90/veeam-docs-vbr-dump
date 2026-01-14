---
title: "backupservers_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backupservers_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a backup server having the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backupServers/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backupServers/{ID}?format=Entity |

Related Resources

* [/backupServers](backupservers.md)
* [/jobs](jobs.md)
* [/repositories](repositories.md)
* [/managedServers](managedservers.md)
* [/backupServers/{ID}/credentials](backupservers_id_credentials.md)
* [/backupServers/{ID}/passwords](backupservers_id_passwords.md)
* [/backupServers/{ID}/externalRepositories](backupservers_id_externalrepositories.md)

Methods

The following methods are supported for the /backupServers/{ID} resource:

* [GET /backupServers{ID}](get_backupservers_id.md)
* [PUT /backupServers{ID}](put_backupservers_id.md)
* [DELETE /backupServers/{ID}](delete_backupservers_id.md)
* [POST /backupServers/{ID}?action=veeamzip](post_backupservers_id_zip.md)
* [POST /backupServers/{ID}?action=quickbackup](post_backupservers_id_quickbackup.md)
* [POST /backupServers/{ID}?action=collect](post_backupservers_id_collect.md)

Resource Representation

The /backupServers/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" UID="urn:veeam:BackupServer:ce15a8c7-aa49-495e-b05b-ee3398c91018"> |

Entity resource representation:

|  |
| --- |
| <BackupServer xmlns="http://www.veeam.com/ent/v1.0" Type="BackupServer" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018?format=Entity" Name="srv02.tech.local" UID="urn:veeam:BackupServer:ce15a8c7-aa49-495e-b05b-ee3398c91018">   <Links>     <Link Rel="Alternate" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />     <Link Rel="Edit" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" />     <Link Rel="Delete" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" />     <Link Rel="Down" Type="JobReferenceList" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018/jobs" />     <Link Rel="Down" Type="ManagedServerReferenceList" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018/managedServers" />     <Link Rel="Down" Type="RepositoryReferenceList" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018/repositories" />     <Link Rel="Down" Type="CredentialsList" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018/credentials" />     <Link Rel="Create" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018/credentials?action=create" />     <Link Rel="Down" Type="PasswordKeyList" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018/passwords" />     <Link Rel="Create" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018/passwords?action=create" />     <Link Rel="VeeamZip" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018?action=veeamzip" />     <Link Rel="QuickBackup" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018?action=quickbackup" />     <Link Rel="Start" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018?action=collect" />   </Links>   <Description />   <Port>9392</Port>   <Version>8.0</Version> </BackupServer> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
