---
title: "/replicaSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/replicasessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /replicaSessions


Represents a list of all replication job sessions performed on all backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/replicaSessions |

Related Resources

[/replicaSessions/{ID}](replicasessions_id.md)

Methods

The following methods are supported for the /replicaSessions resource:

[GET /replicaSessions](get_replicasessions.md)

Resource Representation

The /replicaSessions resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="ReplicaJobSessionReference" Href="https://localhost:9398/api/replicaSessions/53d58f4f-3976-47b7-aec4-3d29a963b0e5" Name="SQL Replication@2025-10-19 05:41:52" UID="urn:veeam:ReplicaJobSession:53d58f4f-3976-47b7-aec4-3d29a963b0e5">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="JobReference" Href="https://localhost:9398/api/jobs/b04c217b-0538-4650-bec4-19deff4ea1ac" Name="SQL Replication" />       <Link Rel="Alternate" Type="ReplicaJobSession" Href="https://localhost:9398/api/replicaSessions/53d58f4f-3976-47b7-aec4-3d29a963b0e5?format=Entity" Name="SQL Replication@2025-10-19 05:41:52" />       <Link Rel="Down" Type="ReplicaTaskSessionReferenceList" Href="https://localhost:9398/api/replicaSessions/53d58f4f-3976-47b7-aec4-3d29a963b0e5/repicaTaskSessions" />     </Links>   </Ref>   <Ref Type="ReplicaJobSessionReference" Href="https://localhost:9398/api/replicaSessions/0bcf5a1e-866c-4b40-8bc3-ce64753b9a6b" Name="Fileserver02 Replication@2025-10-19 06:46:31" UID="urn:veeam:ReplicaJobSession:0bcf5a1e-866c-4b40-8bc3-ce64753b9a6b">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="JobReference" Href="https://localhost:9398/api/jobs/2c49a44e-1e59-4527-a6bc-6b2f9b579ee1" Name="Fileserver02 Replication" />       <Link Rel="Alternate" Type="ReplicaJobSession" Href="https://localhost:9398/api/replicaSessions/0bcf5a1e-866c-4b40-8bc3-ce64753b9a6b?format=Entity" Name="Fileserver02 Replication@2025-10-19 06:46:31" />       <Link Rel="Down" Type="ReplicaTaskSessionReferenceList" Href="https://localhost:9398/api/replicaSessions/0bcf5a1e-866c-4b40-8bc3-ce64753b9a6b/repicaTaskSessions" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

