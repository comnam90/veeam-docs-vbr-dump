---
title: "/catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/catalog_vms_vmname_vmrestorepoints_id_guestfs.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs


Represents a hierarchy of the VM guest OS files within a VM backup.

The /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/ resource becomes available after the client sends the POST request to the /catalog/vms/{vmname}/vmRestorePoints/{ID}?action=browse URL. For details, see [POST /catalog/vms/{vmname}/vmRestorePoints/{ID}?action=browse](post_catalog_vms_vmname_vmrestorepoints_id_actoinbrowse.md).

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/ |

Related Resources

[/catalog/vms/{vmname}/vmRestorePoints/{ID}](catalog_vms_vmname_vmrestorepoints_id.md)

Methods

The following methods are supported for the /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/ resource:

[GET /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/](get_catalog_vms_vmname_vmrestorepoints_id_guestfs.md)

Resource Representation

The /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/ resource has a resource representation of the following type:

|  |
| --- |
| <FileSystemEntry xmlns="http://www.veeam.com/ent/v1.0"> |


