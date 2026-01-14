---
title: "backupsessions_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backupsessions_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a backup job session having the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backupSessions/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backupSessions/{ID}?format=Entity |

Related Resources

* [/backupServers](backupservers.md)
* [/jobs/{ID}](jobs_id.md)
* [/restorepoints/{ID}](restorepoints_id.md)
* [/tasks](tasks.md)

Methods

The following methods are supported for the /backupSessions/{ID} resource:

[GET /backupSessions/{ID}](get_backupsessions_id.md)

Resource Representation

The /backupSessions/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/d46e39e0-1131-4585-91a7-e828ce7eafae" Name="Fileserver Backup@2014-10-19 05:22:52" UID="urn:veeam:BackupJobSession:d46e39e0-1131-4585-91a7-e828ce7eafae"> |

Entity resource representation:

|  |
| --- |
| <BackupJobSession xmlns="http://www.veeam.com/ent/v1.0" Type="BackupJobSession" Href="https://localhost:9398/api/backupSessions/d46e39e0-1131-4585-91a7-e828ce7eafae?format=Entity" Name="Fileserver Backup@2014-10-19 05:22:52" UID="urn:veeam:BackupJobSession:d46e39e0-1131-4585-91a7-e828ce7eafae">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />     <Link Rel="Up" Type="JobReference" Href="https://localhost:9398/api/jobs/4856ab37-2235-45e8-affe-d515878b01a9" Name="Fileserver Backup" />     <Link Rel="Alternate" Type="BackupJobSessionReference" Href="https://localhost:9398/api/backupSessions/d46e39e0-1131-4585-91a7-e828ce7eafae" Name="Fileserver Backup@2014-10-19 05:22:52" />     <Link Rel="Down" Type="BackupTaskSessionReferenceList" Href="https://localhost:9398/api/backupSessions/d46e39e0-1131-4585-91a7-e828ce7eafae/taskSessions" />     <Link Rel="Stop" Href="https://localhost:9398/api/backupSessions/d46e39e0-1131-4585-91a7-e828ce7eafae?action=stop" />     <Link Rel="Related" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/a2d7d2a9-8407-4585-9649-515ecb04b35a" Name="Oct 19 2014  5:23AM" />   </Links>   <JobUid>urn:veeam:Job:4856ab37-2235-45e8-affe-d515878b01a9</JobUid>   <JobName>Fileserver Backup</JobName>   <JobType>Backup</JobType>   <CreationTimeUTC>2014-10-19T05:22:52Z</CreationTimeUTC>   <EndTimeUTC>2014-10-19T05:40:48Z</EndTimeUTC>   <State>Stopped</State>   <Result>Success</Result>   <Progress>100</Progress>   <IsRetry>false</IsRetry> </BackupJobSession> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
