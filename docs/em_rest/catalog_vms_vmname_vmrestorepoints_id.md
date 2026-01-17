---
title: "/catalog/vms/{vmname}/vmRestorePoints/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/catalog_vms_vmname_vmrestorepoints_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a VM restore point having the specified ID. The restore point is created for a VM having the specified name, and guest OS files of the VM have been indexed during backup.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/catalog/vms/{vmname}/vmRestorePoints/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/catalog/vms/{vmname}/vmRestorePoints/{ID}?Format=Entity |

Related Resources

[/catalog/vms/{vmname}/vmRestorePoints](catalog_vms_vmname_vmrestorepoints.md)

Methods

The following methods are supported for the /catalog/vms/{vmname}/vmRestorePoints/{ID} resource:

* [GET /catalog/vms/{vmname}/vmRestorePoints /{ID}](get_catalog_vms_vmname_vmrestorepoints_id.md)
* [POST /catalog/vms/{vmname}/vmRestorePoints/{ID}?action=browse](post_catalog_vms_vmname_vmrestorepoints_id_actoinbrowse.md)

Resource Representation

The /catalog/vms/{vmname}/vmRestorePoints/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="CatalogVmRestorePointReference" Href="https://localhost:9398/api/catalog/vms/srv04/vmRestorePoints/7caf66d5-f700-442c-9aa9-8867f031377f" Name="10/19/2014 7:34:00 AM" UID="urn:veeam:CatalogVmRestorePoint:7caf66d5-f700-442c-9aa9-8867f031377f"> |

Entity resource representation:

|  |
| --- |
| <CatalogVmRestorePoint xmlns="http://www.veeam.com/ent/v1.0" Type="CatalogVmRestorePoint" Href="https://localhost:9398/api/catalog/vms/srv04/vmRestorePoints/7caf66d5-f700-442c-9aa9-8867f031377f?format=Entity" Name="srv04" UID="urn:veeam:CatalogVmRestorePoint:7caf66d5-f700-442c-9aa9-8867f031377f">   <Links>     <Link Rel="Alternate" Type="CatalogVmRestorePointReference" Href="https://localhost:9398/api/catalog/vms/srv04/vmRestorePoints/7caf66d5-f700-442c-9aa9-8867f031377f" Name="srv04" />     <Link Rel="Up" Type="CatalogVm" Href="https://localhost:9398/api/catalog/vms/srv04?format=Entity" Name="srv04" />     <Link Rel="Browse" Href="https://localhost:9398/api/catalog/vms/srv04/vmRestorePoints/7caf66d5-f700-442c-9aa9-8867f031377f?action=browse" />     <Link Rel="Related" Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/7caf66d5-f700-442c-9aa9-8867f031377f?format=Entity" Name="srv04" />   </Links>   <BackupDateUTC>2014-10-19T07:34:00Z</BackupDateUTC> </CatalogVmRestorePoint> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
