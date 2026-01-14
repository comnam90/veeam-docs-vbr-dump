---
title: "agents_agentrestorepoints_id_mounts"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/agents_agentrestorepoints_id_mounts.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

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
| <AgentRestorePointMounts xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
