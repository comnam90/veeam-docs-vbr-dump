---
title: "/backupSessions/{ID}/taskSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backupsessions_id_tasksessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /backupSessions/{ID}/taskSessions


Represents a list of all task sessions performed during the [Backup and Agent](get_backupsessions_id.md#JobType) backup session having a specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backupSessions/{ID}/taskSessions |

Related Resources

[/backupSessions/{ID}](backupsessions_id.md)

Methods

The following methods are supported for the /backupSessions/{ID}/taskSessions resource:

[GET /backupSessions/{ID}/taskSessions](get_backupsessions_id_tasksessions.md)

Resource Representation

The /backupSessions/{ID}/taskSessions resource has a resource representation of the following type:

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:BackupTaskSession:2007feec-790c-49c3-b116-c4ed3b70ddf0" Name="restapizip@2025-01-17 19:13:29" Href="https://localhost:9398/api/backupTaskSessions/2007feec-790c-49c3-b116-c4ed3b70ddf0" Type="BackupTaskSessionReference">     <Links>       <Link Href="https://localhost:9398/api/backupServers/4ad6fa62-9164-4ea0-87c8-1e2d071d60de" Name="restapivbr.tech.local" Type="BackupServerReference" Rel="Up"/>       <Link Href="https://localhost:9398/api/backupSessions/34b45e89-f138-4539-99a6-224e913582d9" Name="restapizip\_2025-01-17T202515@2025-01-17 19:13:15" Type="BackupJobSessionReference" Rel="Up"/>       <Link Href="https://localhost:9398/api/backupTaskSessions/2007feec-790c-49c3-b116-c4ed3b70ddf0?format=Entity" Name="restapizip@2025-01-17 19:13:29" Type="BackupTaskSession" Rel="Alternate"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

