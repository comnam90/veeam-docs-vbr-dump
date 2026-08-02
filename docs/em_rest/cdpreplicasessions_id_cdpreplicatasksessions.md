---
title: "/cdpReplicaSessions/{ID}/cdpReplicaTaskSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cdpreplicasessions_id_cdpreplicatasksessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /cdpReplicaSessions/{ID}/cdpReplicaTaskSessions


Represents a collection of CDP replication task sessions of the CDP replication session that has the specified ID. Within the CDP replication session, each task processes one object (VM or VM container) until a new long-term restore point is created. After a long-term restore point is created, Veeam Backup & Replication starts new CDP replication task sessions.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cdpReplicaSessions/{ID}/cdpReplicaTaskSessions |

Related Resources

[/cdpReplicaTaskSessions/{ID}](cdpreplicatasksessions_id.md)

Methods

The following methods are supported for the /cdpReplicaSessions/{ID}/cdpReplicaTaskSessions resource:

[GET /cdpReplicaSessions/{ID}/cdpReplicaTaskSessions](get_cdpreplicasessions_id_cdpreplicatasksessions.md)

Resource Representation

The /cdpReplicaSessions/{ID}/cdpReplicaTaskSessions resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CdpReplicaTaskSessionReference" Href="https://localhost:9398/api/cdpReplicaTaskSessions/2ec4d35f-b5d8-4cb3-9d11-12e1d5792625" Name="virt03-ubuntu01@2025-02-12 00:00:10" UID="urn:veeam:CdpReplicaTaskSession:2ec4d35f-b5d8-4cb3-9d11-12e1d5792625">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f" Name="CDP Policy 1@2025-02-11 19:08:36" />       <Link Rel="Alternate" Type="CdpReplicaTaskSession" Href="https://localhost:9398/api/cdpReplicaTaskSessions/2ec4d35f-b5d8-4cb3-9d11-12e1d5792625?format=Entity" Name="virt03-ubuntu01@2025-02-12 00:00:10" />     </Links>   </Ref>   <Ref Type="CdpReplicaTaskSessionReference" Href="https://localhost:9398/api/cdpReplicaTaskSessions/54c47e13-e599-4e75-9c67-9377d54e9fde" Name="virt03-vm01@2025-02-11 19:15:52" UID="urn:veeam:CdpReplicaTaskSession:54c47e13-e599-4e75-9c67-9377d54e9fde">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f" Name="CDP Policy 1@2025-02-11 19:08:36" />       <Link Rel="Alternate" Type="CdpReplicaTaskSession" Href="https://localhost:9398/api/cdpReplicaTaskSessions/54c47e13-e599-4e75-9c67-9377d54e9fde?format=Entity" Name="virt03-vm01@2025-02-11 19:15:52" />     </Links>   </Ref>   <Ref Type="CdpReplicaTaskSessionReference" Href="https://localhost:9398/api/cdpReplicaTaskSessions/a583a5af-b2dc-43d2-8150-ae12acf75ec5" Name="virt03-vm01@2025-02-11 19:08:40" UID="urn:veeam:CdpReplicaTaskSession:a583a5af-b2dc-43d2-8150-ae12acf75ec5">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f" Name="CDP Policy 1@2025-02-11 19:08:36" />       <Link Rel="Alternate" Type="CdpReplicaTaskSession" Href="https://localhost:9398/api/cdpReplicaTaskSessions/a583a5af-b2dc-43d2-8150-ae12acf75ec5?format=Entity" Name="virt03-vm01@2025-02-11 19:08:40" />     </Links>   </Ref>   <Ref Type="CdpReplicaTaskSessionReference" Href="https://localhost:9398/api/cdpReplicaTaskSessions/3e7687b2-7eb1-499c-ae2a-b01c99336a86" Name="virt03-ubuntu01@2025-02-11 23:49:16" UID="urn:veeam:CdpReplicaTaskSession:3e7687b2-7eb1-499c-ae2a-b01c99336a86">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f" Name="CDP Policy 1@2025-02-11 19:08:36" />       <Link Rel="Alternate" Type="CdpReplicaTaskSession" Href="https://localhost:9398/api/cdpReplicaTaskSessions/3e7687b2-7eb1-499c-ae2a-b01c99336a86?format=Entity" Name="virt03-ubuntu01@2025-02-11 23:49:16" />     </Links>   </Ref>   <Ref Type="CdpReplicaTaskSessionReference" Href="https://localhost:9398/api/cdpReplicaTaskSessions/41b57841-7f15-4400-b224-e55851605364" Name="virt03-ubuntu01@2025-02-11 23:36:35" UID="urn:veeam:CdpReplicaTaskSession:41b57841-7f15-4400-b224-e55851605364">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f" Name="CDP Policy 1@2025-02-11 19:08:36" />       <Link Rel="Alternate" Type="CdpReplicaTaskSession" Href="https://localhost:9398/api/cdpReplicaTaskSessions/41b57841-7f15-4400-b224-e55851605364?format=Entity" Name="virt03-ubuntu01@2025-02-11 23:36:35" />     </Links>   </Ref>   <Ref Type="CdpReplicaTaskSessionReference" Href="https://localhost:9398/api/cdpReplicaTaskSessions/92aca37b-6ccd-470c-8808-ea9f0b5bf1b3" Name="virt03-vm01@2025-02-12 00:00:08" UID="urn:veeam:CdpReplicaTaskSession:92aca37b-6ccd-470c-8808-ea9f0b5bf1b3">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/cca0b96b-4924-4461-8899-b831bc00176e" Name="enterprise03.tech.local" />       <Link Rel="Up" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/6b872a71-51e8-437a-8d45-5c6494b92f3f" Name="CDP Policy 1@2025-02-11 19:08:36" />       <Link Rel="Alternate" Type="CdpReplicaTaskSession" Href="https://localhost:9398/api/cdpReplicaTaskSessions/92aca37b-6ccd-470c-8808-ea9f0b5bf1b3?format=Entity" Name="virt03-vm01@2025-02-12 00:00:08" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

