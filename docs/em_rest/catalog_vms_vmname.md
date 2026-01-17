---
title: "/catalog/vms/{vmname}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/catalog_vms_vmname.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a VM having the specified name whose guest OS files have been indexed during backup.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/catalog/vms/{vmname} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/catalog/vms/{vmname}?format=Entity |

Related Resources

[/catalog/vms/{vmname}/vmRestorePoints](catalog_vms_vmname_vmrestorepoints.md)

Methods

The following methods are supported for the /catalog/vms/{vmname} resource:

[GET /catalog/vms/{vmname}](get_catalog_vms_vmname.md)

Resource Representation

The /catalog/vms/{vmname} resource has a resource representation of the following type.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="CatalogVmReference" Href="https://localhost:9398/api/catalog/vms/srv04" Name="srv04" UID="urn:veeam:CatalogVm:srv04"> |

Entity resource representation:

|  |
| --- |
| <CatalogVm xmlns="http://www.veeam.com/ent/v1.0" Type="CatalogVm" Href="https://localhost:9398/api/catalog/vms/srv04?format=Entity" Name="srv04" UID="urn:veeam:CatalogVm:srv04" VmDisplayName="srv04">   <Links>     <Link Rel="Alternate" Type="CatalogVmReference" Href="https://localhost:9398/api/catalog/vms/srv04" Name="srv04" />     <Link Rel="Down" Type="CatalogVmRestorePointReferenceList" Href="https://localhost:9398/api/catalog/vms/srv04/vmRestorePoints" />   </Links> </CatalogVm> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
