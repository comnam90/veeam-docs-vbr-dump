---
title: "/agents/protectionGroups/{ID}/discoveredComputers"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/agents_protectiongroups_id_discoveredcomputers.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /agents/protectionGroups/{ID}/discoveredComputers


Represents a collection of all discovered computers in a protection group having the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/agents/protectionGroups/{ID}/discoveredComputers |

Related Resources

* [/backupServers/{ID}](backupservers_id.md)
* [/agents/discoveredComputers/{ID}](agents_discoveredcomputers_id.md)

Methods

The following methods are supported for the /agents/protectionGroups/{ID}/discoveredComputers resource:

[GET /agents/protectionGroups/{ID}/discoveredComputers](get_agents_protectiongroups_id_discoveredcomputers.md)

Resource Representation

The /agents/protectionGroups/{ID}/discoveredComputers resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:DiscoveredComputer:9ee13ff9-aaa7-403d-80c1-9f49833b90a9" Name="sql12ten.local" Href="http://local.host:9399/api/backupTaskSessions/9ee13ff9-aaa7-403d-80c1-9f49833b90a9" Type="DiscoveredComputerReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/discoveredComputers/9ee13ff9-aaa7-403d-80c1-9f49833b90a9?format=Entity" Name="sql12ten.local" Type="DiscoveredComputer" Rel="Alternate"/>     </Links>   </Ref>   <Ref UID="urn:veeam:DiscoveredComputer:a2db19ca-200f-4231-b655-ec47651cecb9" Name="sql2025.local" Href="http://local.host:9399/api/backupTaskSessions/a2db19ca-200f-4231-b655-ec47651cecb9" Type="DiscoveredComputerReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/discoveredComputers/a2db19ca-200f-4231-b655-ec47651cecb9?format=Entity" Name="sql2025.local" Type="DiscoveredComputer" Rel="Alternate"/>     </Links>   </Ref>   ... </EntityReferences> |

Page updated 2026-07-29

