---
title: "/agents/discoveredComputers/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/agents_discoveredcomputers_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /agents/discoveredComputers/{ID}


Represents a protected computer having the specified ID.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/agents/discoveredComputers/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/agents/discoveredComputers/{ID}?format=Entity |

Related Resources

* [/backupServers](backupservers.md)
* [/agents/discoveredComputers](agents_discoveredcomputers.md)

Methods

The following methods are supported for the /agents/discoveredComputers/{ID} resource:

[GET /agents/protectionGroups/{ID}](get_agents_protectiongroups_id.md)

Resource Representation

The /agents/discoveredComputers/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="DiscoveredComputerReference" Href="https://localhost:9398/api/backupTaskSessions/b85df3d1-c094-437c-b836-eaca6c3762ca" Name="enterprise03.tech.local" UID="urn:veeam:DiscoveredComputer:b85df3d1-c094-437c-b836-eaca6c3762ca"> |

Entity resource representation:

|  |
| --- |
| <DiscoveredComputer xmlns="http://www.veeam.com/ent/v1.0" Type="DiscoveredComputer" Href="https://localhost:9398/api/backupTaskSessions/b85df3d1-c094-437c-b836-eaca6c3762ca?format=Entity" Name="enterprise03.tech.local" UID="urn:veeam:DiscoveredComputer:b85df3d1-c094-437c-b836-eaca6c3762ca">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />     <Link Rel="Alternate" Type="DiscoveredComputerReference" Href="https://localhost:9398/api/agents/discoveredComputers/b85df3d1-c094-437c-b836-eaca6c3762ca" Name="enterprise03.tech.local" />     <Link Rel="Up" Type="AgentProtectionGroupReference" Href="https://localhost:9398/api/agents/protectionGroups/d0671b61-8f92-45a7-a199-ab2aad8037c6" Name="Protection Group 1" />   </Links>   <HostStatus>Online</HostStatus>   <AgentVersion>5.0.0.4301</AgentVersion>   <AgentStatus>Installed</AgentStatus>   <OsVersion>Microsoft Windows Server 2012 R2 (64-bit)</OsVersion>   <IpAddress>172.17.53.89</IpAddress>   <HierarchyObjRef>urn:AgentForWindows:VeeamAgent:00000000-0000-0000-0000-000000000000.b85df3d1-c094-437c-b836-eaca6c3762ca</HierarchyObjRef> </DiscoveredComputer> |


