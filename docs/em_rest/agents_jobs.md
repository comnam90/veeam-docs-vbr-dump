---
title: "/agents/jobs"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/agents_jobs.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /agents/jobs


Represents a collection of all Veeam Agent backup jobs configured in Veeam Backup & Replication on all backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/agents/jobs |

Related Resources

[/agents/jobs/{ID}](agents_jobs_id.md)

Methods

The following methods are supported for the /agents/jobs resource:

[GET /agents/jobs](get_agents_jobs.md)

Resource Representation

The /agents/jobs resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:AgentBackupJob:92346ee0-5191-4556-a9c6-ed1a38cdc71b" Name="Agent Backup Job 1" Href="http://local.host:9399/api/agents/jobs/92346ee0-5191-4556-a9c6-ed1a38cdc71b" Type="AgentBackupJobReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/35dfeff8-5104-403b-a208-06e2d9a1da0b" Name="win10x64.tech.local" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/jobs/92346ee0-5191-4556-a9c6-ed1a38cdc71b?format=Entity" Name="Agent Backup Job 1" Type="Job" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/agents/jobs/92346ee0-5191-4556-a9c6-ed1a38cdc71b/backupSessions" Type="BackupJobSessionReferenceList" Rel="Down"/>     </Links>   </Ref>   <Ref UID="urn:veeam:AgentBackupJob:4dc5d947-9c23-4e1b-976a-ee5911f6a996" Name="Agent Backup rhel72 lvm" Href="http://local.host:9399/api/agents/jobs/4dc5d947-9c23-4e1b-976a-ee5911f6a996" Type="AgentBackupJobReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/3e1e451a-4718-4475-836b-9547ccae6872" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/jobs/4dc5d947-9c23-4e1b-976a-ee5911f6a996?format=Entity" Name="Agent Backup rhel72 lvm" Type="Job" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/agents/jobs/4dc5d947-9c23-4e1b-976a-ee5911f6a996/backupSessions" Type="BackupJobSessionReferenceList" Rel="Down"/>     </Links>   </Ref>   <Ref UID="urn:veeam:AgentBackupJob:95f84a48-6e05-459a-8f26-f2330c9efdf5" Name="Agent Backup Job SQL" Href="http://local.host:9399/api/agents/jobs/95f84a48-6e05-459a-8f26-f2330c9efdf5" Type="AgentBackupJobReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/3e1e451a-4718-4475-836b-9547ccae6872" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/jobs/95f84a48-6e05-459a-8f26-f2330c9efdf5?format=Entity" Name="Agent Backup Job SQL" Type="Job" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/agents/jobs/95f84a48-6e05-459a-8f26-f2330c9efdf5/backupSessions" Type="BackupJobSessionReferenceList" Rel="Down"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

