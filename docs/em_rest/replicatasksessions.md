---
title: "/replicaTaskSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/replicatasksessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /replicaTaskSessions


Represents a collection of replication tasks run on backup servers connected to Veeam Backup Enterprise Manager.

You should distinguish the /replicaTaskSessions resource from the /replicaSessions resource. The /replicaSessions resource provides information about a specific cycle of a replication job. The /replicaTaskSessions resource provides information about a specific task within a replication job session. Typically, one task processes one object in the replication job: VM or VM container.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/replicaTaskSessions |

Related Resources

[/replicaTaskSessions/{ID}](replicatasksessions_id.md)

Methods

The following methods are supported for the /replicaTaskSessions resource:

[GET /replicaTaskSessions](get_replicatasksessions.md)

Resource Representation

The /replicaTaskSessions resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="ReplicaTaskSessionReference" Href="https://localhost:9398/api/repicaTaskSessions/1f2b40a8-2370-4280-a3f9-5f7c611d3f79" Name="sql02@2025-10-19 05:42:46" UID="urn:veeam:ReplicaTaskSession:1f2b40a8-2370-4280-a3f9-5f7c611d3f79">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="ReplicaJobSessionReference" Href="https://localhost:9398/api/replicaSessions/b04c217b-0538-4650-bec4-19deff4ea1ac" Name="SQL Replication" />       <Link Rel="Alternate" Type="ReplicaTaskSession" Href="https://localhost:9398/api/repicaTaskSessions/1f2b40a8-2370-4280-a3f9-5f7c611d3f79?format=Entity" Name="sql02@2025-10-19 05:42:46" />     </Links>   </Ref>   <Ref Type="ReplicaTaskSessionReference" Href="https://localhost:9398/api/repicaTaskSessions/24590151-20cd-4e57-8a2f-8b65869a1879" Name="srv04@2025-10-19 06:47:21" UID="urn:veeam:ReplicaTaskSession:24590151-20cd-4e57-8a2f-8b65869a1879">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="ReplicaJobSessionReference" Href="https://localhost:9398/api/replicaSessions/2c49a44e-1e59-4527-a6bc-6b2f9b579ee1" Name="Fileserver02 Replication" />       <Link Rel="Alternate" Type="ReplicaTaskSession" Href="https://localhost:9398/api/repicaTaskSessions/24590151-20cd-4e57-8a2f-8b65869a1879?format=Entity" Name="srv04@2025-10-19 06:47:21" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

