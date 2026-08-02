---
title: "/agents/protectionGroups"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/agents_protectiongroups.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /agents/protectionGroups


Represents a list of protection groups configured on all backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/agents/protectionGroups |

Related Resources

[/agents/protectionGroups/{ID}](agents_protectiongroups_id.md)

Methods

The following methods are supported for the /agents/protectionGroups resource:

[GET /agents/protectionGroups](get_agents_protectiongroups.md)

Resource Representation

The /agents/protectionGroups resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:AgentProtectionGroup:1ca088be-7a63-43b9-bda1-2db2ad7a1bd5" Name="sql servers" Href="http://local.host:9399/api/agents/protectionGroups/1ca088be-7a63-43b9-bda1-2db2ad7a1bd5" Type="AgentProtectionGroupReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/protectionGroups/1ca088be-7a63-43b9-bda1-2db2ad7a1bd5?format=Entity" Name="sql servers" Type="AgentProtectionGroup" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/agents/protectionGroups/1ca088be-7a63-43b9-bda1-2db2ad7a1bd5/discoveredComputers" Type="DiscoveredComputerReferenceList" Rel="Down"/>     </Links>   </Ref>   <Ref UID="urn:veeam:AgentProtectionGroup:9093c50b-fc31-41e0-89d9-44c195a9eed5" Name="Protection Group" Href="http://local.host:9399/api/agents/protectionGroups/9093c50b-fc31-41e0-89d9-44c195a9eed5" Type="AgentProtectionGroupReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/protectionGroups/9093c50b-fc31-41e0-89d9-44c195a9eed5?format=Entity" Name="Protection Group" Type="AgentProtectionGroup" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/agents/protectionGroups/9093c50b-fc31-41e0-89d9-44c195a9eed5/discoveredComputers" Type="DiscoveredComputerReferenceList" Rel="Down"/>     </Links>   </Ref>   <Ref UID="urn:veeam:AgentProtectionGroup:8d8798d4-4911-4d80-b9d4-452629081648" Name="Manually Added" Href="http://local.host:9399/api/agents/protectionGroups/8d8798d4-4911-4d80-b9d4-452629081648" Type="AgentProtectionGroupReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/protectionGroups/8d8798d4-4911-4d80-b9d4-452629081648?format=Entity" Name="Manually Added" Type="AgentProtectionGroup" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/agents/protectionGroups/8d8798d4-4911-4d80-b9d4-452629081648/discoveredComputers" Type="DiscoveredComputerReferenceList" Rel="Down"/>     </Links>   </Ref>   <Ref UID="urn:veeam:AgentProtectionGroup:3cbecd3a-2df9-4a11-9e95-abcdf2d0e8a7" Name="Protection Group rhel 72 lvm" Href="http://local.host:9399/api/agents/protectionGroups/3cbecd3a-2df9-4a11-9e95-abcdf2d0e8a7" Type="AgentProtectionGroupReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/protectionGroups/3cbecd3a-2df9-4a11-9e95-abcdf2d0e8a7?format=Entity" Name="Protection Group rhel 72 lvm" Type="AgentProtectionGroup" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/agents/protectionGroups/3cbecd3a-2df9-4a11-9e95-abcdf2d0e8a7/discoveredComputers" Type="DiscoveredComputerReferenceList" Rel="Down"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

