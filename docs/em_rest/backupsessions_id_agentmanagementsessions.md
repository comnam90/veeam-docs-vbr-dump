---
title: "/backupSessions/{ID}/agentManagementSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backupsessions_id_agentmanagementsessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /backupSessions/{ID}/agentManagementSessions


Represents a list of all [AgentManagement](get_backupsessions_id.md#JobType) job sessions performed during the [AgentBackup](get_backupsessions_id.md#JobType) backup session having a specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backupSessions/{ID}/agentManagementSessions |

Related Resources

[/backupSessions/{ID}](backupsessions_id.md)

Methods

The following methods are supported for the /backupSessions/{ID}/agentManagementSessions resource:

[GET /backupSessions/{ID}/agentManagementSessions](get_backupsessions_id_agentmanagementsessions.md)

Resource Representation

The /backupSessions/{ID}/agentManagementSessions resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:BackupJobSession:0e6b4c7d-0d9c-4ab9-94a7-71e39895485b" Name="Agent Backup Job SQL - sql12ten.local@2025-12-20 14:30:45" Href="http://local.host:9399/api/backupSessions/0e6b4c7d-0d9c-4ab9-94a7-71e39895485b" Type="BackupJobSessionReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/jobs/77dc8834-2102-4edf-8a0d-aba909b2d1ed" Name="Agent Backup Job SQL - sql12ten.local" Type="JobReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupSessions/8ba90554-4cb0-4979-b4cc-00887fcd1caa" Name="Parent session" Type="BackupJobSessionReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupSessions/0e6b4c7d-0d9c-4ab9-94a7-71e39895485b?format=Entity" Name="Agent Backup Job SQL - sql12ten.local@2025-12-20 14:30:45" Type="BackupJobSession" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backupSessions/0e6b4c7d-0d9c-4ab9-94a7-71e39895485b/taskSessions" Type="BackupTaskSessionReferenceList" Rel="Down"/>     </Links>   </Ref>   <Ref UID="urn:veeam:BackupJobSession:b66c1ef7-290a-4646-a34b-df28813df301" Name="Agent Backup Job SQL - sql2025.local@2025-12-20 14:30:45" Href="http://local.host:9399/api/backupSessions/b66c1ef7-290a-4646-a34b-df28813df301" Type="BackupJobSessionReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/jobs/abd14f39-6fc0-4e79-b777-96126c62fdd3" Name="Agent Backup Job SQL - sql2025.local" Type="JobReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupSessions/8ba90554-4cb0-4979-b4cc-00887fcd1caa" Name="Parent session" Type="BackupJobSessionReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupSessions/b66c1ef7-290a-4646-a34b-df28813df301?format=Entity" Name="Agent Backup Job SQL - sql2025.local@2025-12-20 14:30:45" Type="BackupJobSession" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backupSessions/b66c1ef7-290a-4646-a34b-df28813df301/taskSessions" Type="BackupTaskSessionReferenceList" Rel="Down"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

