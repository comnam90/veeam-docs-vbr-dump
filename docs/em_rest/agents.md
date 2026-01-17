---
title: "/agents"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/agents.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

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
| <Agents Href="http://local.host:9399/api/agents" Type="AgentsService" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
