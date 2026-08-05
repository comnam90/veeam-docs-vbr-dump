---
title: "/agents/agentRestorePoints/{ID}/mounts"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/agents_agentrestorepoints_id_mounts.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /agents/agentRestorePoints/{ID}/mounts


Represents a collection of mount points created for restore points of Veeam Agent machines.

Mount points are specific Veeam Backup Enterprise Manager objects that provide access to machine guest OS files. The /agents/agentRestorePoints/{ID}/mounts resource collection becomes available only after the client performs file-level restore for the Veeam Agent machine by sending the POST HTTP request to the /agents/agentRestorePoints/{ID}/mounts resource. For details, see [POST /agents/agentRestorePoints/{ID}/mounts](post_agents_agentrestorepoints_id_mounts.md).

During the restore process, Veeam Backup & Replication mounts disks of the backed-up machine to the backup server. As a result, the machine guest OS files can be accessed through the mount point by the following path: C:\VeeamFLR\<vm-name>. The client can browse the guest file system, get the necessary files and folders and restore them.

The /agents/agentRestorePoints/{ID}/mounts resource collection is available only within the currently existing logon session. After the logon session expires, all created mount points become inaccessible.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/agents/agentRestorePoints/{ID}/mounts |

Related Resources

* [/agents/agentRestorePoints/{ID}](agents_agentrestorepoints_id.md)
* [/agents/agentRestorePoints/{ID}/mounts/{ID}](agents_agentrestorepoints_id_mounts_id.md)
* [/catalog/vms/{vmname}/vmRestorePoints/{ID}](catalog_vms_vmname_vmrestorepoints_id.md)

Methods

The following methods are supported for the /agents/agentRestorePoints/{ID}/mounts resource:

[GET /agents/agentRestorePoints/{ID}/mounts](get_agents_agentrestorepoints_id_mounts.md)

Resource Representation

The /agents/agentRestorePoints/{ID}/mounts resource has a resource representation of the following type:

|  |
| --- |
| <AgentRestorePointMounts xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <AgentRestorePointMount Href="https://localhost:9398/api/agents/agentRestorePoints/dd3cf3d0-0533-424e-abc3-249c4c62b797/mounts/1" Type="AgentRestorePointMount">     <Links>       <Link Href="https://localhost:9398/api/agents/agentRestorePoints/dd3cf3d0-0533-424e-abc3-249c4c62b797/mounts/1" Rel="Delete"/>     </Links>     <FSRoots>       <DirectoryEntry Href="https://localhost:9398/api/agents/agentRestorePoints/dd3cf3d0-0533-424e-abc3-249c4c62b797/mounts/1/C:" Type="DirectoryEntry">         <Path>C:</Path>         <Name>C:</Name>       </DirectoryEntry>     </FSRoots>   </AgentRestorePointMount>   <AgentRestorePointMount Href="https://localhost:9398/api/agents/agentRestorePoints/dd3cf3d0-0533-424e-abc3-249c4c62b797/mounts/2" Type="AgentRestorePointMount">     <Links>       <Link Href="https://localhost:9398/api/agents/agentRestorePoints/dd3cf3d0-0533-424e-abc3-249c4c62b797/mounts/2" Rel="Delete"/>     </Links>     <FSRoots>       <DirectoryEntry Href="https://localhost:9398/api/agents/agentRestorePoints/dd3cf3d0-0533-424e-abc3-249c4c62b797/mounts/2/C:" Type="DirectoryEntry">         <Path>C:</Path>         <Name>C:</Name>       </DirectoryEntry>     </FSRoots>   </AgentRestorePointMount> </AgentRestorePointMounts> |

Page updated 2026-07-29

