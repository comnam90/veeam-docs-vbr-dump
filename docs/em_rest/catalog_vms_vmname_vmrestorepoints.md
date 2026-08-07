---
title: "/catalog/vms/{vmname}/vmRestorePoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/catalog_vms_vmname_vmrestorepoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /catalog/vms/{vmname}/vmRestorePoints


Represents a collection of restore points for VMs whose guest OS files have been indexed during backup.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/catalog/vms/{vmname}/vmRestorePoints |

Related Resources

[/catalog/vms/{vmname}/vmRestorePoints/{ID}](catalog_vms_vmname_vmrestorepoints_id.md)

Methods

The following methods are supported for the /catalog/vms/{vmname}/vmRestorePoints resource:

[GET /catalog/vms/{vmname}/vmRestorePoints](get_catalog_vms_vmname_vmrestorepoints.md)

Resource Representation

The /catalog/vms/{vmname}/vmRestorePoints resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CatalogVmRestorePointReference" Href="https://localhost:9398/api/catalog/vms/srv04/vmRestorePoints/fb87163e-687d-4006-96c9-0451b5423b85" Name="10/19/2025 5:25:00 AM" UID="urn:veeam:CatalogVmRestorePoint:fb87163e-687d-4006-96c9-0451b5423b85">     <Links>       <Link Rel="Up" Href="https://localhost:9398/api/catalog/vms/srv04" />       <Link Rel="Alternate" Href="https://localhost:9398/api/catalog/vms/srv04/vmRestorePoints/fb87163e-687d-4006-96c9-0451b5423b85?format=Entity" />     </Links>   </Ref>   <Ref Type="CatalogVmRestorePointReference" Href="https://localhost:9398/api/catalog/vms/srv04/vmRestorePoints/7caf66d5-f700-442c-9aa9-8867f031377f" Name="10/19/2025 7:34:00 AM" UID="urn:veeam:CatalogVmRestorePoint:7caf66d5-f700-442c-9aa9-8867f031377f">     <Links>       <Link Rel="Up" Href="https://localhost:9398/api/catalog/vms/srv04" />       <Link Rel="Alternate" Href="https://localhost:9398/api/catalog/vms/srv04/vmRestorePoints/7caf66d5-f700-442c-9aa9-8867f031377f?format=Entity" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

