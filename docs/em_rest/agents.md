---
title: "/agents"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/agents.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /agents


The /agents resource provides a set of links to the following Veeam Agent Management resources:

* [DiscoveredComputer](agents_discoveredcomputers.md)
* [AgentProtectionGroup](agents_protectiongroups.md)
* [AgentBackupJob](agents_jobs.md)
* [Backup](agents_backups.md)
* [BackupFile](agents_backupfiles.md)
* [BackupJobSession](agents_backupsessions.md)
* [RestorePoint](agents_restorepoints.md)
* [AgentRestorePoint](agents_agentrestorepoints.md)

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/agents |

Related Resources

None.

Methods

The following methods are supported for the /agents resource:

[GET /agents](get_agents.md)

Resource Representation

The /agents resource has a resource representation of the following type:

|  |
| --- |
| <Agents Href="http://local.host:9399/api/agents" Type="AgentsService" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Links>     <Link Href="http://local.host:9399/api/agents/jobs" Type="JobReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/agentRestorePoints" Type="AgentRestorePointReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/backups" Type="BackupReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/restorePoints" Type="RestorePointReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/backupFiles" Type="RestorePointReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/backupSessions" Type="BackupJobSessionReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/protectionGroups" Type="AgentProtectionGroupReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/discoveredComputers" Type="DiscoveredComputerReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/jobs?format=Entity" Type="JobList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/agentRestorePoints?format=Entity" Type="AgentRestorePointList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/backups?format=Entity" Type="BackupList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/restorePoints?format=Entity" Type="RestorePointList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/backupFiles?format=Entity" Type="RestorePointList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/backupSessions?format=Entity" Type="BackupJobSessionList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/protectionGroups?format=Entity" Type="AgentProtectionGroupList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/discoveredComputers?format=Entity" Type="DiscoveredComputerList" Rel="Down"/>   </Links> </Agents> |

Page updated 2026-07-29

