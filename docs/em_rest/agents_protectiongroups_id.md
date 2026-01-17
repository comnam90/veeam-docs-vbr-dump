---
title: "/agents/protectionGroups/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/agents_protectiongroups_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a protection group having the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/agents/protectionGroups/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/agents/protectionGroups/{ID}?format=Entity |

Related Resources

* [/backupServers](backupservers.md)
* [/agents/protectionGroups](agents_protectiongroups.md)

Methods

The following methods are supported for the /agents/protectionGroups/{ID} resource:

[GET /agents/protectionGroups/{ID}](get_agents_protectiongroups_id.md)

Resource Representation

The /agents/protectionGroups/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef UID="urn:veeam:AgentProtectionGroup:1ca088be-7a63-43b9-bda1-2db2ad7a1bd5" Name="sql servers" Href="http://local.host:9399/api/agents/protectionGroups/1ca088be-7a63-43b9-bda1-2db2ad7a1bd5" Type="AgentProtectionGroupReference" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> |

Entity resource representation:

|  |
| --- |
| <AgentProtectionGroup Href="http://local.host:9399/api/agents/protectionGroups/1ca088be-7a63-43b9-bda1-2db2ad7a1bd5?format=Entity" Type="AgentProtectionGroup" Name="sql servers" UID="urn:veeam:AgentProtectionGroup:1ca088be-7a63-43b9-bda1-2db2ad7a1bd5" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Links>     <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>     <Link Href="http://local.host:9399/api/agents/protectionGroups/1ca088be-7a63-43b9-bda1-2db2ad7a1bd5" Name="sql servers" Type="AgentProtectionGroupReference" Rel="Alternate"/>     <Link Href="http://local.host:9399/api/agents/protectionGroups/1ca088be-7a63-43b9-bda1-2db2ad7a1bd5/discoveredComputers?format=Entity" Type="DiscoveredComputerList" Rel="Down"/>   </Links>   <RescanScheduleEnabled>true</RescanScheduleEnabled>   <HierarchyObjRef>urn:AgentForWindows:AgentProtectionGroup:00000000-0000-0000-0000-000000000000.730dc485-84c2-4a9d-86e7-2e35d1d5a0be</HierarchyObjRef> </AgentProtectionGroup> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
