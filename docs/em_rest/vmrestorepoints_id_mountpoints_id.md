---
title: "/vmRestorePoints/{ID}/mounts/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/vmrestorepoints_id_mountpoints_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a mount point resource having the specified ID.

Mount points are specific Veeam Backup Enterprise Manager objects that provide access to VM guest OS files. The /vmRestorePoints/{ID}/mounts/{ID} resource becomes available only after the client performs file-level restore for the VM by sending the POST HTTP request to the /vmRestorePoints/{ID}/mounts resource. For details, see [POST /vmRestorePoints/{ID}/mounts](post_vmrestorepoints_id_mountpoints.md).

During the restore process, Veeam Backup & Replication mounts VM disks to the backup server. As a result, the VM guest OS files can be accessed through the mount point by the following path: C:\VeeamFLR\<vm-name>. The client can browse the VM guest file system, get the necessary files and folders and restore them.

The /vmRestorePoints/{ID}/mounts/{ID} resource is available only within the currently existing logon session. After the logon session expires, all created mount points become inaccessible.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vmRestorePoints/{ID}/mounts/{ID} |

Related Resources

[/vmRestorePoints/{ID}](vmrestorepoints_id.md)

Methods

The following methods are supported for the /vmRestorePoints/{ID}/mounts/{ID}} resource:

* [GET /vmRestorePoints/{ID}/mounts/{ID}](get_vmrestorepoints_id_mountpoints_id.md)
* [DELETE /vmRestorePoints/{ID}/mounts/{ID}](delete_vmrestorepoints_id_mountpoints_id.md)

Resource Representation

The /vmRestorePoints/{ID}/mounts/{ID} resource has a resource representation of the following type:

|  |
| --- |
| <VmRestorePointMount xmlns="http://www.veeam.com/ent/v1.0" Type="VmRestorePointMount" Href="https://localhost:9398/api/vmRestorePoints/fb87163e-687d-4006-96c9-0451b5423b85/mounts/1"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
