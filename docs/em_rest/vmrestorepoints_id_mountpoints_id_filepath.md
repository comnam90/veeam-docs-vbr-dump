---
title: "/vmRestorePoints/{ID}/mounts/{ID}/{filepath}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/vmrestorepoints_id_mountpoints_id_filepath.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /vmRestorePoints/{ID}/mounts/{ID}/{filepath}


Represents a VM guest OS file or folder that can be restored.

The /vmRestorePoints/{ID}/mounts/{ID}/{filepath} resource becomes available only after the client performs file-level restore for the VM by sending the POST HTTP request to the /vmRestorePoints/{ID}/mounts resource. For details, see [POST /vmRestorePoints/{ID}/mounts](post_vmrestorepoints_id_mountpoints.md).

During the restore process, Veeam Backup & Replication mounts VM disks from the backup in the repository to the mount server associated with that repository. As a result, the VM guest OS files can be accessed through the mount point by the following path: C:\VeeamFLR\<vm-name>. The client can browse the VM guest file system, get the necessary files and folders and restore them.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vmRestorePoints/{ID}/mounts/{ID}/{filepath} |

Related Resources

* [/vmRestorePoints/{ID}/mounts/{ID}](vmrestorepoints_id_mountpoints_id.md)
* [/catalog/vms/{vmname}/vmRestorePoints/{ID}](catalog_vms_vmname_vmrestorepoints_id.md)

Methods

The following methods are supported for the /vmRestorePoints/{ID}/mounts/{ID}/{filepath} resource:

* [GET /vmrestorepoints/{ID}/mountpoints/{ID}/{filepath}](get_vmrestorepoints_id_mountpoints_id_filepath.md)
* [POST /vmrestorepoints/{ID}/mountpoints/{ID}/{filepath}?action=restore](post_vmrestorepoints_id_mountpoints_id_filepath_actionrestore.md)

Resource Representation

The /vmRestorePoints/{ID}/mounts/{ID}/{filepath} resource has a resource representation of the following type:

|  |
| --- |
| <FileSystemEntries xmlns="http://www.veeam.com/ent/v1.0" Href="https://localhost:9398/api/vmRestorePoints/fb87163e-687d-4006-96c9-0451b5423b85/mounts/1/E:?action=listDirs&pageSize=10&page=1"> |


