---
title: "/agents/discoveredComputers"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/agents_discoveredcomputers.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /agents/discoveredComputers


Represents a list of all protected computers in all protection groups configured on all backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/agents/discoveredComputers |

Related Resources

[/agents/discoveredComputers/{ID}](agents_discoveredcomputers_id.md)

Methods

The following methods are supported for the /agents/discoveredComputers resource:

[GET /agents/discoveredComputers](get_agents_discoveredcomputers.md)

Resource Representation

The /agents/discoveredComputers resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:DiscoveredComputer:b0ad8ec4-5f17-45e6-be9b-1334ea320af0" Name="win7x86.local" Href="http://local.host:9399/api/backupTaskSessions/b0ad8ec4-5f17-45e6-be9b-1334ea320af0" Type="DiscoveredComputerReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/discoveredComputers/b0ad8ec4-5f17-45e6-be9b-1334ea320af0?format=Entity" Name="win7x86.local" Type="DiscoveredComputer" Rel="Alternate"/>     </Links>   </Ref>   <Ref UID="urn:veeam:DiscoveredComputer:9ee13ff9-aaa7-403d-80c1-9f49833b90a9" Name="sql12ten.local" Href="http://local.host:9399/api/backupTaskSessions/9ee13ff9-aaa7-403d-80c1-9f49833b90a9" Type="DiscoveredComputerReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/discoveredComputers/9ee13ff9-aaa7-403d-80c1-9f49833b90a9?format=Entity" Name="sql12ten.tech.local" Type="DiscoveredComputer" Rel="Alternate"/>     </Links>   </Ref>   <Ref UID="urn:veeam:DiscoveredComputer:53518661-b43f-4e50-a8cf-cffead274366" Name="rhel72" Href="http://local.host:9399/api/backupTaskSessions/53518661-b43f-4e50-a8cf-cffead274366" Type="DiscoveredComputerReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/discoveredComputers/53518661-b43f-4e50-a8cf-cffead274366?format=Entity" Name="rhel72" Type="DiscoveredComputer" Rel="Alternate"/>     </Links>   </Ref>   <Ref UID="urn:veeam:DiscoveredComputer:53518661-b43f-4e50-a8cf-cffead274366" Name="rhel72" Href="http://local.host:9399/api/backupTaskSessions/53518661-b43f-4e50-a8cf-cffead274366" Type="DiscoveredComputerReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/discoveredComputers/53518661-b43f-4e50-a8cf-cffead274366?format=Entity" Name="rhel72" Type="DiscoveredComputer" Rel="Alternate"/>     </Links>   </Ref>   <Ref UID="urn:veeam:DiscoveredComputer:a2db19ca-200f-4231-b655-ec47651cecb9" Name="sql2025.local" Href="http://local.host:9399/api/backupTaskSessions/a2db19ca-200f-4231-b655-ec47651cecb9" Type="DiscoveredComputerReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/discoveredComputers/a2db19ca-200f-4231-b655-ec47651cecb9?format=Entity" Name="sql2025.local" Type="DiscoveredComputer" Rel="Alternate"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

