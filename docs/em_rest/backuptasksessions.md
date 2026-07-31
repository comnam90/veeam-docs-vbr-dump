---
title: "/backupTaskSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backuptasksessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /backupTaskSessions


Represents a collection of backup tasks run on backup servers connected to Veeam Backup Enterprise Manager.

You should distinguish the /backupTaskSessions resource from the /backupSessions resource. The /backupSessions resource provides information about a specific cycle of a backup job. The /backupTaskSessions resource provides information about a specific task within a backup job session. Typically, one task processes one object in the backup job: VM or VM container.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backupTaskSessions |

Related Resources

[/backupTaskSessions/{ID}](backuptasksessions_id.md)

Methods

The following methods are supported for the /backupTaskSessions resource:

[GET /backupTaskSessions](get_backuptasksessions.md)

Resource Representation

The /backupTaskSessions resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="BackupTaskSessionReference" Href="https://localhost:9398/api/backupTaskSessions/9c1abbfb-48a2-4042-b2f0-1ac12adecdb6" Name="VM01@2025-10-19 06:07:13" UID="urn:veeam:BackupTaskSession:9c1abbfb-48a2-4042-b2f0-1ac12adecdb6">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/bce9741f-d6aa-43ca-a229-1706c2eea0e7" Name="vApp 01 Backup Job@2025-10-19 06:05:03" />       <Link Rel="Alternate" Type="BackupTaskSession" Href="https://localhost:9398/api/backupTaskSessions/9c1abbfb-48a2-4042-b2f0-1ac12adecdb6?format=Entity" Name="w2k3-x64-from-temmplate@2025-10-19 06:07:13" />     </Links>   </Ref>   <Ref Type="BackupTaskSessionReference" Href="https://localhost:9398/api/backupTaskSessions/20caf784-f9b4-4826-b544-1ad8a99031b7" Name="dns@2025-03-01 11:27:04" UID="urn:veeam:BackupTaskSession:20caf784-f9b4-4826-b544-1ad8a99031b7">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/672d10c5-3b5c-474b-9550-e16707898b91" Name="Daily NetApp Snapshots@2025-03-01 11:25:36" />       <Link Rel="Alternate" Type="BackupTaskSession" Href="https://localhost:9398/api/backupTaskSessions/20caf784-f9b4-4826-b544-1ad8a99031b7?format=Entity" Name="dns@2025-03-01 11:27:04" />     </Links>   </Ref>   <Ref Type="BackupTaskSessionReference" Href="https://localhost:9398/api/backupTaskSessions/76051d5e-1760-4f02-819c-264f2448df97" Name="oracle@2025-10-18 13:09:58" UID="urn:veeam:BackupTaskSession:76051d5e-1760-4f02-819c-264f2448df97">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/4dcc1993-c7e8-4e4d-a82b-48716dd148a2" Name="Oracle Backup@2025-10-18 13:09:06" />       <Link Rel="Alternate" Type="BackupTaskSession" Href="https://localhost:9398/api/backupTaskSessions/76051d5e-1760-4f02-819c-264f2448df97?format=Entity" Name="oracle@2025-10-18 13:09:58" />     </Links>   </Ref>   <Ref Type="BackupTaskSessionReference" Href="https://localhost:9398/api/backupTaskSessions/b9033a9f-50bc-4c18-b8de-29107c033a13" Name="dhcp@2025-03-01 11:27:04" UID="urn:veeam:BackupTaskSession:b9033a9f-50bc-4c18-b8de-29107c033a13">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/672d10c5-3b5c-474b-9550-e16707898b91" Name="Daily NetApp Snapshots@2025-03-01 11:25:36" />       <Link Rel="Alternate" Type="BackupTaskSession" Href="https://localhost:9398/api/backupTaskSessions/b9033a9f-50bc-4c18-b8de-29107c033a13?format=Entity" Name="dhcp@2025-03-01 11:27:04" />     </Links>   </Ref>   <Ref Type="BackupTaskSessionReference" Href="https://localhost:9398/api/backupTaskSessions/88767486-89d6-4340-92f0-2ad615a8f21b" Name="srv04@2025-10-19 05:23:44" UID="urn:veeam:BackupTaskSession:88767486-89d6-4340-92f0-2ad615a8f21b">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/d46e39e0-1131-4585-91a7-e828ce7eafae" Name="Fileserver Backup@2025-10-19 05:22:52" />       <Link Rel="Alternate" Type="BackupTaskSession" Href="https://localhost:9398/api/backupTaskSessions/88767486-89d6-4340-92f0-2ad615a8f21b?format=Entity" Name="srv04@2025-10-19 05:23:44" />     </Links>   </Ref>   <Ref Type="BackupTaskSessionReference" Href="https://localhost:9398/api/backupTaskSessions/28803e33-6366-4604-83d1-2b670a4469f2" Name="sql02@2025-01-01 18:11:12" UID="urn:veeam:BackupTaskSession:28803e33-6366-4604-83d1-2b670a4469f2">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/8738ca5c-bda0-44cf-973d-6d46175d7522" Name="Daily NetApp Snapshots@2025-01-01 18:10:30" />       <Link Rel="Alternate" Type="BackupTaskSession" Href="https://localhost:9398/api/backupTaskSessions/28803e33-6366-4604-83d1-2b670a4469f2?format=Entity" Name="sql02@2025-01-01 18:11:12" />     </Links>   </Ref> </EntityReferences |

Page updated 2026-07-29

