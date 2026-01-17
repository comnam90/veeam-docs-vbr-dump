---
title: "/agents/agentRestorePoints/{ID}/mounts/{ID}/{filepath}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/agents_agentrestorepoints_id_mounts_id_filepath.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a guest OS file or folder that can be restored.

The /agents/agentRestorePoints/{ID}/mounts/{ID}/{filepath} resource becomes available only after the client performs file-level restore for the machine by sending the POST HTTP request to the /agents/agentRestorePoints/{ID}/mounts resource. For details, see [POST /agents/agentRestorePoints/{ID}/mounts](post_agents_agentrestorepoints_id_mounts.md).

During the restore process, Veeam Backup & Replication mounts disks of the backed-up machine from the backup in the repository to the mount server associated with that repository. As a result, the machine guest OS files can be accessed through the mount point by the following path: C:\VeeamFLR\<vm-name>. The client can browse the guest file system, get the necessary files and folders and restore them.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/agents/agentRestorePoints/{ID}/mounts/{ID}/{filepath} |

Related Resources

* [/agents/agentRestorePoints/{ID}/mounts/{ID}](agents_agentrestorepoints_id_mounts_id.md)
* [/catalog/vms/{vmname}/vmRestorePoints/{ID}](catalog_vms_vmname_vmrestorepoints_id.md)

Methods

The following methods are supported for the /agents/agentRestorePoints/{ID}/mounts/{ID}/{filepath} resource:

* [GET /agents/agentRestorePoints/{ID}/mounts/{ID}/{filepath}](get_agents_agentrestorepoints_id_mounts_id_filepath.md)
* [POST /agents/agentRestorePoints/{ID}/mounts/{ID}/{filepath}?action=restore](post_agents_agentrestorepoints_id_mounts_id_filepath_actionrestore.md)

Resource Representation

The /agents/agentRestorePoints/{ID}/mounts/{ID}/{filepath} resource has a resource representation of the following type:

|  |
| --- |
| <FileSystemEntries Href="https://localhost:9398/api/agents/agentRestorePoints/dd3cf3d0-0533-424e-abc3-249c4c62b797/mounts/1/C:?action=listDirs&pageSize=10&page=1" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
