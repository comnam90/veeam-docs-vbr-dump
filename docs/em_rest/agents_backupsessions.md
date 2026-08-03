---
title: "/agents/backupSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/agents_backupsessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /agents/backupSessions


Represents a collection of sessions performed for Veeam Agent backup jobs configured in Veeam Backup & Replication on all backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/agents/backupSessions |

Related Resources

[/backupSessions/{ID}](backupsessions_id.md)

Methods

The following methods are supported for the /agents/backupSessions resource:

[GET /agents/backupSessions](get_agents_backupsessions.md)

Resource Representation

The /agents/backupSessions resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:BackupJobSession:8ba90554-4cb0-4979-b4cc-00887fcd1caa" Name="Agent Backup Job SQL@2025-12-20 14:30:29" Href="http://w10x64v1709.local:9399/api/backupSessions/8ba90554-4cb0-4979-b4cc-00887fcd1caa" Type="BackupJobSessionReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/jobs/95f84a48-6e05-459a-8f26-f2330c9efdf5" Name="Agent Backup Job SQL" Type="JobReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupSessions/8ba90554-4cb0-4979-b4cc-00887fcd1caa/agentManagementSessions" Type="BackupJobSessionReferenceList" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backupSessions/8ba90554-4cb0-4979-b4cc-00887fcd1caa?format=Entity" Name="Agent Backup Job SQL@2025-12-20 14:30:29" Type="BackupJobSession" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backupSessions/8ba90554-4cb0-4979-b4cc-00887fcd1caa/taskSessions" Type="BackupTaskSessionReferenceList" Rel="Down"/>     </Links>   </Ref>   <Ref UID="urn:veeam:BackupJobSession:fc98d417-63c6-432e-8378-017eb33b51f3" Name="Agent Backup rhel72 lvm@2025-12-16 05:00:00" Href="http://local.host:9399/api/backupSessions/fc98d417-63c6-432e-8378-017eb33b51f3" Type="BackupJobSessionReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/jobs/4dc5d947-9c23-4e1b-976a-ee5911f6a996" Name="Agent Backup rhel72 lvm" Type="JobReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupSessions/fc98d417-63c6-432e-8378-017eb33b51f3/agentManagementSessions" Type="BackupJobSessionReferenceList" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backupSessions/fc98d417-63c6-432e-8378-017eb33b51f3?format=Entity" Name="Agent Backup rhel72 lvm@2025-12-16 05:00:00" Type="BackupJobSession" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backupSessions/fc98d417-63c6-432e-8378-017eb33b51f3/taskSessions" Type="BackupTaskSessionReferenceList" Rel="Down"/>     </Links>   </Ref>   <Ref UID="urn:veeam:BackupJobSession:b0b3b4d5-fcfd-429c-928f-01a52ddfe560" Name="Agent Backup rhel72 lvm - rhel72@2025-12-16 10:00:08" Href="http://local.host:9399/api/backupSessions/b0b3b4d5-fcfd-429c-928f-01a52ddfe560" Type="BackupJobSessionReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/jobs/a1e698f3-282c-484c-b942-e42c5c77449a" Name="Agent Backup rhel72 lvm - rhel72" Type="JobReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupSessions/addf6ac2-89d9-4f5c-b90b-2e63f84ac3da" Name="Parent session" Type="BackupJobSessionReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupSessions/b0b3b4d5-fcfd-429c-928f-01a52ddfe560?format=Entity" Name="Agent Backup rhel72 lvm - rhel72@2025-12-16 10:00:08" Type="BackupJobSession" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backupSessions/b0b3b4d5-fcfd-429c-928f-01a52ddfe560/taskSessions" Type="BackupTaskSessionReferenceList" Rel="Down"/>     </Links>   </Ref>   <Ref UID="urn:veeam:BackupJobSession:8293f9f3-7cc8-4023-85c4-022438415420" Name="Agent Backup Job SQL@2025-12-16 03:00:03" Href="http://local.host:9399/api/backupSessions/8293f9f3-7cc8-4023-85c4-022438415420" Type="BackupJobSessionReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/jobs/95f84a48-6e05-459a-8f26-f2330c9efdf5" Name="Agent Backup Job SQL" Type="JobReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupSessions/8293f9f3-7cc8-4023-85c4-022438415420/agentManagementSessions" Type="BackupJobSessionReferenceList" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backupSessions/8293f9f3-7cc8-4023-85c4-022438415420?format=Entity" Name="Agent Backup Job SQL@2025-12-16 03:00:03" Type="BackupJobSession" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backupSessions/8293f9f3-7cc8-4023-85c4-022438415420/taskSessions" Type="BackupTaskSessionReferenceList" Rel="Down"/>     </Links>   </Ref>   <Ref UID="urn:veeam:BackupJobSession:1e036782-9084-42e5-97c5-0230250a1bd4" Name="Agent Backup rhel72 lvm - rhel72@2025-12-16 08:00:16" Href="http://local.host:9399/api/backupSessions/1e036782-9084-42e5-97c5-0230250a1bd4" Type="BackupJobSessionReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/jobs/a1e698f3-282c-484c-b942-e42c5c77449a" Name="Agent Backup rhel72 lvm - rhel72" Type="JobReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupSessions/3b4fd6a2-bda4-422c-a0a0-c2ae1a8ce5cd" Name="Parent session" Type="BackupJobSessionReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupSessions/1e036782-9084-42e5-97c5-0230250a1bd4?format=Entity" Name="Agent Backup rhel72 lvm - rhel72@2025-12-16 08:00:16" Type="BackupJobSession" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backupSessions/1e036782-9084-42e5-97c5-0230250a1bd4/taskSessions" Type="BackupTaskSessionReferenceList" Rel="Down"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-28

