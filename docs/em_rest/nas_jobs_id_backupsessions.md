---
title: "/nas/jobs/{ID}/backupSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/nas_jobs_id_backupsessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /nas/jobs/{ID}/backupSessions


Represents a list of all file share backup job sessions performed for the file share backup job with the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/nas/jobs/{ID}/backupSessions |

Related Resources

[/backupSessions/{ID}](backupsessions_id.md)

Methods

The following methods are supported for the /nas/jobs/{ID}/backupSessions resource:

[GET /nas/jobs/{ID}/backupSessions](get_nas_jobs_id_backupsessions.md)

Resource Representation

The /nas/jobs/{ID}/backupSessions resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="BackupJobSessionReference" Href="https://srv12.tech.local:9398/api/backupSessions/19b6f0f8-777f-4aed-bc76-4584d7867e45" Name="NFS Share Backup@2025-01-30 20:31:10" UID="urn:veeam:BackupJobSession:19b6f0f8-777f-4aed-bc76-4584d7867e45">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />       <Link Rel="Up" Type="JobReference" Href="https://srv12.tech.local:9398/api/jobs/d6b01759-40f0-43ee-940e-496bdd13973c" Name="NFS Share Backup" />       <Link Rel="Alternate" Type="BackupJobSession" Href="https://srv12.tech.local:9398/api/backupSessions/19b6f0f8-777f-4aed-bc76-4584d7867e45?format=Entity" Name="NFS Share Backup@2025-01-30 20:31:10" />       <Link Rel="Down" Type="BackupTaskSessionReferenceList" Href="https://srv12.tech.local:9398/api/backupSessions/19b6f0f8-777f-4aed-bc76-4584d7867e45/taskSessions" />     </Links>   </Ref>   <Ref Type="BackupJobSessionReference" Href="https://srv12.tech.local:9398/api/backupSessions/ede4c840-1947-44e8-b179-4c77f667161d" Name="NFS Share Backup@2025-01-31 17:34:49" UID="urn:veeam:BackupJobSession:ede4c840-1947-44e8-b179-4c77f667161d">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />       <Link Rel="Up" Type="JobReference" Href="https://srv12.tech.local:9398/api/jobs/d6b01759-40f0-43ee-940e-496bdd13973c" Name="NFS Share Backup" />       <Link Rel="Alternate" Type="BackupJobSession" Href="https://srv12.tech.local:9398/api/backupSessions/ede4c840-1947-44e8-b179-4c77f667161d?format=Entity" Name="NFS Share Backup@2025-01-31 17:34:49" />       <Link Rel="Down" Type="BackupTaskSessionReferenceList" Href="https://srv12.tech.local:9398/api/backupSessions/ede4c840-1947-44e8-b179-4c77f667161d/taskSessions" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

