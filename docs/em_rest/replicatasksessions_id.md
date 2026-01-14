---
title: "replicatasksessions_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/replicatasksessions_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a replication task session having the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/replicaTaskSessions/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/replicaTaskSessions/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/replicaSessions/{ID}](replicasessions_id.md)

Methods

The following methods are supported for the /replicaTaskSessions/{ID} resource:

[GET /replicaTaskSessions/{ID}](get_replicatasksessions_id.md)

Resource Representation

The /replicaTaskSessions/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="ReplicaTaskSessionReference" Href="https://localhost:9398/api/repicaTaskSessions/24590151-20cd-4e57-8a2f-8b65869a1879" Name="srv04@2014-10-19 06:47:21" UID="urn:veeam:ReplicaTaskSession:24590151-20cd-4e57-8a2f-8b65869a1879"> |

Entity resource representation:

|  |
| --- |
| <ReplicaTaskSession xmlns="http://www.veeam.com/ent/v1.0" Type="ReplicaTaskSession" Href="https://localhost:9398/api/repicaTaskSessions/24590151-20cd-4e57-8a2f-8b65869a1879?format=Entity" Name="srv04@2014-10-19 06:47:21" UID="urn:veeam:ReplicaTaskSession:24590151-20cd-4e57-8a2f-8b65869a1879" VmDisplayName="srv04">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />     <Link Rel="Up" Type="ReplicaJobSessionReference" Href="https://localhost:9398/api/replicaSessions/0bcf5a1e-866c-4b40-8bc3-ce64753b9a6b" Name="Fileserver02 Replication@2014-10-19 06:46:31" />     <Link Rel="Alternate" Type="ReplicaTaskSessionReference" Href="https://localhost:9398/api/repicaTaskSessions/24590151-20cd-4e57-8a2f-8b65869a1879" Name="srv04@2014-10-19 06:47:21" />     <Link Rel="Related" Type="VmReplicaPoint" Href="https://localhost:9398/api/vmReplicaPoints/623cbbec-c8ff-4cf4-96be-d433f3b775c7?format=Entity" Name="srv04@2014-10-19 06:48:24" />   </Links>   <JobSessionUid>urn:veeam:ReplicaJobSession:0bcf5a1e-866c-4b40-8bc3-ce64753b9a6b</JobSessionUid>   <CreationTimeUTC>2014-10-19T06:47:21Z</CreationTimeUTC>   <EndTimeUTC>2014-10-19T07:02:33Z</EndTimeUTC>   <State>Completed</State>   <Result>Success</Result>   <Reason />   <TotalSize>64424509440</TotalSize> </ReplicaTaskSession> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
