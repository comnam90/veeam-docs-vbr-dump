---
title: "cdpreplicatasksessions_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cdpreplicatasksessions_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a CDP replication task session having the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cdpReplicaTaskSessions/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cdpReplicaTaskSessions/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/cdpReplicaSessions/{ID}](cdpreplicasessions_id.md)

Methods

The following methods are supported for the /cdpReplicaTaskSessions/{ID} resource:

[GET /cdpReplicaTaskSessions/{ID}](get_cdpreplicatasksessions_id.md)

Resource Representation

The /cdpReplicaTaskSessions/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="CdpReplicaTaskSessionReference" Href="https://localhost:9398/api/cdpReplicaTaskSessions/2ec4d35f-b5d8-4cb3-9d11-12e1d5792625" Name="virt03-ubuntu01@2021-02-12 00:00:10" UID="urn:veeam:CdpReplicaTaskSession:2ec4d35f-b5d8-4cb3-9d11-12e1d5792625"> |

Entity resource representation:

|  |
| --- |
| <CdpReplicaTaskSession xmlns="http://www.veeam.com/ent/v1.0" Type="CdpReplicaTaskSession" Href="https://localhost:9398/api/replicaTaskSessions/2ec4d35f-b5d8-4cb3-9d11-12e1d5792625?format=Entity" Name="virt03-ubuntu01@2021-02-12 00:00:10" UID="urn:veeam:CdpReplicaTaskSession:2ec4d35f-b5d8-4cb3-9d11-12e1d5792625" VmDisplayName="virt03-ubuntu01">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />     <Link Rel="Up" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f" Name="CDP Policy 1@2021-02-11 19:08:36" />     <Link Rel="Alternate" Type="CdpReplicaTaskSessionReference" Href="https://localhost:9398/api/cdpReplicaTaskSessions/2ec4d35f-b5d8-4cb3-9d11-12e1d5792625" Name="virt03-ubuntu01@2021-02-12 00:00:10" />   </Links>   <PolicySessionUid>urn:veeam:CdpReplicaSession:6b872a71-51e8-437a-8d45-5c6494b92f3f</PolicySessionUid>   <CreationTimeUTC>2021-02-12T00:00:10.457Z</CreationTimeUTC>   <State>InProgress</State>   <Result>Success</Result>   <TotalSize>17179869184</TotalSize> </CdpReplicaTaskSession> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
