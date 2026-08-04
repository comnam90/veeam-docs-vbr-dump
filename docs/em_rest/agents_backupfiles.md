---
title: "/agents/backupFiles"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/agents_backupfiles.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /agents/backupFiles


Represents a collection of backup files created by Veeam Agent managed by Veeam Backup & Replication. Backup files are created on or imported to backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/agents/backupFiles |

Related Resources

[/backupFiles/{ID}](backupfiles_id.md)

Methods

The following methods are supported for the /agents/backupFiles resource:

[GET /agents/backupFiles](get_agents_backupfiles.md)

Resource Representation

The /agents/backupFiles resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:BackupFile:760634d7-ec46-4356-87cd-035944e77ab3" Name="Agent Backup rhel72 lvm - rhel72\_1C93D2025-12-15T090027.vib" Href="http://local.host:9399/api/backupFiles/760634d7-ec46-4356-87cd-035944e77ab3" Type="BackupFileReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/8aafc7f2-a455-49a2-b66b-81d6f9b6ba2e" Name="Agent Backup rhel72 lvm - rhel72" Type="BackupReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupFiles/760634d7-ec46-4356-87cd-035944e77ab3?format=Entity" Name="Agent Backup rhel72 lvm - rhel72\_1C93D2025-12-15T090027.vib" Type="BackupFile" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backupFiles/760634d7-ec46-4356-87cd-035944e77ab3/restorePoints" Type="BackupFileReferenceList" Rel="Related"/>       <Link Href="http://local.host:9399/api/backupFiles/760634d7-ec46-4356-87cd-035944e77ab3/agentRestorePoints" Type="AgentRestorePointReferenceList" Rel="Down"/>     </Links>   </Ref>   <Ref UID="urn:veeam:BackupFile:46a24719-566c-4e65-aa57-054053e85e77" Name="Agent Backup rhel72 lvm - rhel72\_36F9D2025-12-17T030022.vib" Href="http://local.host:9399/api/backupFiles/46a24719-566c-4e65-aa57-054053e85e77" Type="BackupFileReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/8aafc7f2-a455-49a2-b66b-81d6f9b6ba2e" Name="Agent Backup rhel72 lvm - rhel72" Type="BackupReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupFiles/46a24719-566c-4e65-aa57-054053e85e77?format=Entity" Name="Agent Backup rhel72 lvm - rhel72\_36F9D2025-12-17T030022.vib" Type="BackupFile" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backupFiles/46a24719-566c-4e65-aa57-054053e85e77/restorePoints" Type="BackupFileReferenceList" Rel="Related"/>       <Link Href="http://local.host:9399/api/backupFiles/46a24719-566c-4e65-aa57-054053e85e77/agentRestorePoints" Type="AgentRestorePointReferenceList" Rel="Down"/>     </Links>   </Ref>   <Ref UID="urn:veeam:BackupFile:7dbf79f8-324c-415a-b3bf-05cd7f7d2cdc" Name="Agent Backup Job SQL - sql12ten.veea\_5510D2025-12-19T100102.vib" Href="http://local.host:9399/api/backupFiles/7dbf79f8-324c-415a-b3bf-05cd7f7d2cdc" Type="BackupFileReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/f6307c50-934e-48ce-90a3-6ad0abe003bb" Name="Agent Backup Job SQL - sql12ten.local" Type="BackupReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupFiles/7dbf79f8-324c-415a-b3bf-05cd7f7d2cdc?format=Entity" Name="Agent Backup Job SQL - sql12ten.veea\_5510D2025-12-19T100102.vib" Type="BackupFile" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backupFiles/7dbf79f8-324c-415a-b3bf-05cd7f7d2cdc/restorePoints" Type="BackupFileReferenceList" Rel="Related"/>       <Link Href="http://local.host:9399/api/backupFiles/7dbf79f8-324c-415a-b3bf-05cd7f7d2cdc/agentRestorePoints" Type="AgentRestorePointReferenceList" Rel="Down"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

