---
title: "/replicaSessions/{ID}/replicaTaskSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/replicasessions_id_replicatasksessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /replicaSessions/{ID}/replicaTaskSessions


Represents a collection of replication task sessions of the replication session that has the specified ID. Within the replication session, each task processes one object (VM or VM container).

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/replicaSessions/{ID}/replicaTaskSessions |

Related Resources

* [/replicaSessions/{ID}](replicasessions_id.md)
* [/replicaTaskSessions](replicatasksessions.md)

Methods

The following methods are supported for the /replicaSessions/{ID}/replicaTaskSessions resource:

[GET /replicaSessions/{ID}/replicaTaskSessions](get_replicasessions_id_replicatasksessions.md)

Resource Representation

The /replicaSessions/{ID}/replicaTaskSessions resource has a resource representation of the following type:

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> <ReplicaTaskSessions xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">     <ReplicaTaskSession Href="https://enterprise06.tech.local:9398/api/replicaTaskSessions/c20dae03-4f75-4191-ae81-862f4b7988ca?format=Entity" Type="ReplicaTaskSession" Name="ubuntu88@2025-11-03 21:00:26" UID="urn:veeam:ReplicaTaskSession:c20dae03-4f75-4191-ae81-862f4b7988ca" VmDisplayName="ubuntu88">         <Links>             <Link Href="https://enterprise06.tech.local:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" Type="BackupServerReference" Rel="Up" />             <Link Href="https://enterprise06.tech.local:9398/api/replicaSessions/f5bf1a4b-c229-452e-a4e8-0354e1752b4e" Name="Replication Job 1@2025-11-03 21:00:11" Type="ReplicaJobSessionReference" Rel="Up" />             <Link Href="https://enterprise06.tech.local:9398/api/replicaTaskSessions/c20dae03-4f75-4191-ae81-862f4b7988ca" Name="ubuntu88@2025-11-03 21:00:26" Type="ReplicaTaskSessionReference" Rel="Alternate" />         </Links>         <JobSessionUid>urn:veeam:ReplicaJobSession:f5bf1a4b-c229-452e-a4e8-0354e1752b4e</JobSessionUid>         <CreationTimeUTC>2025-11-03T21:00:26.19Z</CreationTimeUTC>         <EndTimeUTC>2025-11-03T21:03:16.73Z</EndTimeUTC>         <State>Completed</State>         <Result>Success</Result>         <Reason />         <TotalSize>17179869184</TotalSize>     </ReplicaTaskSession> </ReplicaTaskSessions> |

Page updated 2026-07-29

