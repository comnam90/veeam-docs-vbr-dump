---
title: "/vmReplicaPoints/{ID}/mounts/{ID}/{filepath}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/vmreplicapoints_id_mountpoints_id_filepath.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /vmReplicaPoints/{ID}/mounts/{ID}/{filepath}


Represents a VM guest OS file or folder that can be restored.

The /vmReplicaPoints/{ID}/mounts/{ID}/{filepath} resource becomes available only after the client performs file-level restore for the VM by sending the POST HTTP request to the /vmReplicaPoints/{ID}/mounts resource. For details, see [POST /vmReplicaPoints/{ID}/mounts](post_vmreplicapoints_id_mountpoints.md).

During the restore process, Veeam Backup & Replication mounts VM replica disks to the backup server. As a result, the VM guest OS files can be accessed through the mount point by the following path: C:\VeeamFLR\<vm-name>. The client can browse the VM guest file system, get the necessary files and folders and restore them.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/vmReplicaPoints/{ID}/mounts/{ID}/{filepath} |

Related Resources

[/vmReplicaPoints/{ID}/mounts/{ID}](vmreplicapoints_id_mountpoints_id.md)

Methods

The following methods are supported for the /vmReplicaPoints/{ID}/mounts/{ID}/{filepath} resource:

* [GET /vmReplicaPoints/{ID}/mounts/{ID}/{filepath}](get_vmreplicapoints_id_mountpoints_id_filepath.md)
* [POST /vmReplicaPoints/{ID}/mounts/{ID}/{filepath}?action=restore](post_vmreplicapoints_id_mountpoints_id_filepath_actionrestore.md)

Resource Representation

The /vmReplicaPoints/{ID}/mounts/{ID}/{filepath} resource has a resource representation of the following type:

|  |
| --- |
| <FileSystemEntry xmlns="http://www.veeam.com/ent/v1.0">   <DirectoryEntry Type="DirectoryEntry" Href="https://localhost:9398/api/vmReplicaPoints/623cbbec-c8ff-4cf4-96be-d433f3b775c7/mounts/1/E:/Documentation%202525">     <Links>       <Link Rel="Down" Href="https://localhost:9398/api/vmReplicaPoints/623cbbec-c8ff-4cf4-96be-d433f3b775c7/mounts/1/E:/Documentation%202525?action=listAll&pageSize=100&page=1" />       <Link Rel="Down" Href="https://localhost:9398/api/vmReplicaPoints/623cbbec-c8ff-4cf4-96be-d433f3b775c7/mounts/1/E:/Documentation%202525?action=listDirs&pageSize=10&page=1" />       <Link Rel="Down" Href="https://localhost:9398/api/vmReplicaPoints/623cbbec-c8ff-4cf4-96be-d433f3b775c7/mounts/1/E:/Documentation%202525?action=listFiles&pageSize=10&page=1" />       <Link Rel="Restore" Href="https://localhost:9398/api/vmReplicaPoints/623cbbec-c8ff-4cf4-96be-d433f3b775c7/mounts/1/E:/Documentation%202525?action=restore" />     </Links>     <Path>E:/Documentation 2025</Path>     <Name>Documentation 2025</Name>   </DirectoryEntry> </FileSystemEntry> |

Page updated 2026-07-29

