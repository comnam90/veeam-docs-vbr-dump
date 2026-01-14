---
title: "replicasessions_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/replicasessions_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a replication job session having the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/replicaSessions/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/replicaSessions/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/jobs/{ID}](jobs_id.md)
* [/replicaSessions/{ID}/replicaTaskSessions](replicasessions_id_replicatasksessions.md)
* [/replicaTaskSessions](replicatasksessions.md)

Methods

The following methods are supported for the /replicaSessions/{ID} resource:

[GET /replicaSessions/{ID}](get_replicasessions_id.md)

Resource Representation

The /replicaSessions/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="ReplicaJobSessionReference" Href="https://localhost:9398/api/replicaSessions/0bcf5a1e-866c-4b40-8bc3-ce64753b9a6b" Name="Fileserver02 Replication@2014-10-19 06:46:31" UID="urn:veeam:ReplicaJobSession:0bcf5a1e-866c-4b40-8bc3-ce64753b9a6b"> |

Entity resource representation:

|  |
| --- |
| <ReplicaJobSession xmlns="http://www.veeam.com/ent/v1.0" Type="ReplicaJobSession" Href="https://localhost:9398/api/replicaSessions/0bcf5a1e-866c-4b40-8bc3-ce64753b9a6b?format=Entity" Name="Fileserver02 Replication@2014-10-19 06:46:31" UID="urn:veeam:ReplicaJobSession:0bcf5a1e-866c-4b40-8bc3-ce64753b9a6b">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />     <Link Rel="Up" Type="JobReference" Href="https://localhost:9398/api/jobs/2c49a44e-1e59-4527-a6bc-6b2f9b579ee1" Name="Fileserver02 Replication" />     <Link Rel="Alternate" Type="ReplicaJobSessionReference" Href="https://localhost:9398/api/replicaSessions/0bcf5a1e-866c-4b40-8bc3-ce64753b9a6b" Name="Fileserver02 Replication@2014-10-19 06:46:31" />     <Link Rel="Down" Type="ReplicaTaskSessionReferenceList" Href="https://localhost:9398/api/replicaSessions/0bcf5a1e-866c-4b40-8bc3-ce64753b9a6b/repicaTaskSessions" />   </Links>   <JobUid>urn:veeam:Job:2c49a44e-1e59-4527-a6bc-6b2f9b579ee1</JobUid>   <JobName>Fileserver02 Replication</JobName>   <JobType>Replica</JobType>   <CreationTimeUTC>2014-10-19T06:46:31Z</CreationTimeUTC>   <EndTimeUTC>2014-10-19T07:02:35Z</EndTimeUTC>   <State>Stopped</State>   <Result>Success</Result>   <Progress>100</Progress>   <IsRetry>false</IsRetry> </ReplicaJobSession> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
