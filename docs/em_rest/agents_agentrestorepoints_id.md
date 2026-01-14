---
title: "agents_agentrestorepoints_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/agents_agentrestorepoints_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a restore point having the specified ID. A restore point was created for a machine protected with Veeam Agent managed by Veeam Backup & Replication.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/agents/agentRestorePoints/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/agents/agentRestorePoints/{ID}?format=Entity |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/restorePoints/{ID}](restorepoints_id.md)
* [/backupFiles/{ID}](backupfiles_id.md)
* [/agents/agentRestorePoints/{ID}/mounts](agents_agentrestorepoints_id_mounts.md)

Methods

The following methods are supported for the /agents/agentRestorePoints/{ID} resource:

* [GET /agents/agentRestorePoints/{ID}](get_agents_agentrestorepoints_id.md)
* [POST /agents/agentRestorePoints/{ID}/mounts](post_agents_agentrestorepoints_id_mounts.md)

Resource Representation

The /agents/agentRestorePoints/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef UID="urn:veeam:AgentRestorePoint:b6bfce60-7d42-46d7-9e55-0a40c04b0d7d" Name="rhel72@2018-12-17 02:01:05" Href="http://local.host:9399/api/agents/agentRestorePoints/b6bfce60-7d42-46d7-9e55-0a40c04b0d7d" Type="AgentRestorePointReference" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> |

Entity resource representation:

|  |
| --- |
| <AgentRestorePoint Href="http://local.host:9399/api/agents/agentRestorePoints/b6bfce60-7d42-46d7-9e55-0a40c04b0d7d?format=Entity" Type="AgentRestorePoint" Name="rhel72@2018-12-17 02:01:05" UID="urn:veeam:AgentRestorePoint:b6bfce60-7d42-46d7-9e55-0a40c04b0d7d" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Links>     <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>     <Link Href="http://local.host:9399/api/restorePoints/67e4d9b0-a461-41e6-b5e8-037af89e2a88" Name="Dec 17 2018  2:00AM" Type="RestorePointReference" Rel="Up"/>     <Link Href="http://local.host:9399/api/backupFiles/0e2f90e9-23ee-43fe-8279-d0220b081da2" Name="Agent Backup rhel72 lvm - rhel72\_2D7FD2018-12-17T050032.vib" Type="BackupFileReference" Rel="Up"/>     <Link Href="http://local.host:9399/api/agents/agentRestorePoints/b6bfce60-7d42-46d7-9e55-0a40c04b0d7d" Name="rhel72@2018-12-17 02:01:05" Type="AgentRestorePointReference" Rel="Alternate"/>     <Link Href="http://local.host:9399/api/agents/agentRestorePoints/b6bfce60-7d42-46d7-9e55-0a40c04b0d7d/mounts" Type="AgentRestorePointMountList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/agentRestorePoints/b6bfce60-7d42-46d7-9e55-0a40c04b0d7d/mounts" Type="AgentRestorePointMount" Rel="Create"/>   </Links>   <CreationTimeUTC>2018-12-17T02:01:05Z</CreationTimeUTC>   <Algorithm>Incremental</Algorithm>   <PointType>Increment</PointType> </AgentRestorePoint> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
