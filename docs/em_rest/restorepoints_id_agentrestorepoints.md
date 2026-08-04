---
title: "/restorePoints/{ID}/agentRestorePoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/restorepoints_id_agentrestorepoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /restorePoints/{ID}/agentRestorePoints


Represents a collection of all restore points for Veeam Agent backups created on or imported to backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/restorePoints/{ID}/agentRestorePoints |

Related Resources

[/restorePoints/{ID}](restorepoints_id.md)

Methods

The following methods are supported for the /restorePoints/{ID}/agentRestorePoints resource:

[GET /restorePoints/{ID}/agentRestorePoints](get_restorepoints_id_agentrestorepoints.md)

Resource Representation

The /restorePoints/{ID}/agentRestorePoints resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:AgentRestorePoint:69c8ab97-acce-452e-8224-671a665e66ef" Name="sql12ten.local@2025-12-18 21:03:02" Href="http://local.host:9399/api/agents/agentRestorePoints/69c8ab97-acce-452e-8224-671a665e66ef" Type="AgentRestorePointReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/restorePoints/7be71fcb-7301-4efa-9c24-011dc67f063c" Name="Dec 18 2025  9:01PM" Type="RestorePointReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupFiles/dc00423c-3875-4e77-9122-13947ad797ba" Name="Agent Backup Job SQL - sql12ten.veea\_5778D2025-12-19T000125.vib" Type="BackupFileReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/agentRestorePoints/69c8ab97-acce-452e-8224-671a665e66ef?format=Entity" Name="sql12ten.tech.local@2025-12-18 21:03:02" Type="AgentRestorePoint" Rel="Alternate"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

