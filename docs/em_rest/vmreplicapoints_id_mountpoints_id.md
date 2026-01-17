---
title: "/vmReplicaPoints/{ID}/mounts/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/vmreplicapoints_id_mountpoints_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a mount point resource having the specified ID.

Mount points are specific Veeam Backup Enterprise Manager objects that provide access to VM replica guest OS files. The /vmReplicaPoints/{ID}/mounts/{ID} resource becomes available only after the client performs file-level restore for the VM by sending the POST HTTP request to the /vmReplicaPoints/{ID}/mounts resource. For details, see [POST /vmReplicaPoints/{ID}/mounts](post_vmreplicapoints_id_mountpoints.md).

During the restore process, Veeam Backup & Replication mounts VM disks to the backup server. As a result, the VM guest OS files can be accessed through the mount point by the following path: C:\VeeamFLR\<vm-name>. The client can browse the VM replica guest file system, get the necessary files and folders and restore them.

The /vmReplicaPoints/{ID}/mounts/{ID} resource is available only within the currently existing logon session. After the logon session expires, all created mount points become inaccessible.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vmReplicaPoints/{ID}/mounts/{ID} |

Related Resources

[/vmReplicaPoints/{ID}](vmreplicapoints_id.md)

Methods

The following methods are supported for the /vmReplicaPoints/{ID}/mounts/{ID} resource:

* [GET /vmrestorepoints/{ID}/mountpoints/{ID}](get_vmreplicapoints_id_mountpoints_id.md)
* [DELETE /vmrestorepoints/{ID}/mountpoints/{ID}](delete_vmreplicapoints_id_mountpoints_id.md)

Resource Representation

The /vmReplicaPoints/{ID}/mounts/{ID} resource has a resource representation of the following type:

|  |
| --- |
| <VmReplicaPointMount xmlns="http://www.veeam.com/ent/v1.0" Type="VmReplicaPointMount" Href="https://localhost:9398/api/vmReplicaPoints/623cbbec-c8ff-4cf4-96be-d433f3b775c7/mounts/1"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
