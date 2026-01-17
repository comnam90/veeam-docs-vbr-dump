---
title: "/backupTaskSessions/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backuptasksessions_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /backupTaskSessions/{ID}


Represents a backup task having the specified ID. The task has been performed on the backup server connected to Veeam Backup Enterprise Manager.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backupTaskSessions/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backupTaskSessions/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/backupSessions/{ID}](backupsessions_id.md)

Methods

The following methods are supported for the /backupTaskSessions/{ID} resource:

[GET /backupTaskSessions/{ID}](get_backuptasksessions_id.md)

Resource Representation

The /backupTaskSessions/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="BackupTaskSessionReference" Href="https://localhost:9398/api/backupTaskSessions/88767486-89d6-4340-92f0-2ad615a8f21b" Name="srv04@2014-10-19 05:23:44" UID="urn:veeam:BackupTaskSession:88767486-89d6-4340-92f0-2ad615a8f21b"> |

Entity resource representation:

|  |
| --- |
| <BackupTaskSession xmlns="http://www.veeam.com/ent/v1.0" Type="BackupTaskSession" Href="https://localhost:9398/api/backupTaskSessions/88767486-89d6-4340-92f0-2ad615a8f21b?format=Entity" Name="srv04@2014-10-19 05:23:44" UID="urn:veeam:BackupTaskSession:88767486-89d6-4340-92f0-2ad615a8f21b" VmDisplayName="srv04">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />     <Link Rel="Up" Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/d46e39e0-1131-4585-91a7-e828ce7eafae" Name="Fileserver Backup@2014-10-19 05:22:52" />     <Link Rel="Alternate" Type="BackupTaskSessionReference" Href="https://localhost:9398/api/backupTaskSessions/88767486-89d6-4340-92f0-2ad615a8f21b" Name="srv04@2014-10-19 05:23:44" />     <Link Rel="Related" Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/fb87163e-687d-4006-96c9-0451b5423b85?format=Entity" Name="srv04@2014-10-19 05:25:15" />   </Links>   <JobSessionUid>urn:veeam:BackupJobSession:d46e39e0-1131-4585-91a7-e828ce7eafae</JobSessionUid>   <CreationTimeUTC>2014-10-19T05:23:44Z</CreationTimeUTC>   <EndTimeUTC>2014-10-19T05:40:39Z</EndTimeUTC>   <State>Completed</State>   <Result>Success</Result>   <Reason />   <TotalSize>64424509440</TotalSize> </BackupTaskSession> |


