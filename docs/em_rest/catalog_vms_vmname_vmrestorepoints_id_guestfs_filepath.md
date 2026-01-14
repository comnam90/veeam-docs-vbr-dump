---
title: "catalog_vms_vmname_vmrestorepoints_id_guestfs_filepath"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/catalog_vms_vmname_vmrestorepoints_id_guestfs_filepath.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a VM guest OS file or folder that can be accessed and restored.

The /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/{filepath} resource becomes available after the client sends the POST request to the /catalog/vms/{vmname}/vmRestorePoints/{ID}?action=browse URL. For details, see [POST /catalog/vms/{vmname}/vmRestorePoints/{ID}?action=browse](post_catalog_vms_vmname_vmrestorepoints_id_actoinbrowse.md).

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/{filepath} |

Related Resources

[/catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/](catalog_vms_vmname_vmrestorepoints_id_guestfs.md)

Methods

The following methods are supported for the /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/{filepath} resource:

* [GET /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/{filepath}](get_catalog_vms_vmname_vmrestorepoints_id_guestfs_filepath.md)
* [POST /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/{filepath}?action=restore](post_catalog_vms_vmname_vmrestorepoints_id_guestfs_filepath.md)

Resource Representation

The /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/{filepath} resource has a resource representation of the following type:

|  |
| --- |
| <FileSystemEntries xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
