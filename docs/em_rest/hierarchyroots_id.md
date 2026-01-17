---
title: "/hierarchyRoots/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/hierarchyroots_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a virtualization host having the specified ID. The virtualization host is added to the backup server connected to Veeam Backup Enterprise Manager.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/hierarchyRoots/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/hierarchyRoots/{ID}?format=Entity |

Related Resources

* [/managedServers/{ID}](managedservers_id.md)
* [/backupServers/{ID}](backupservers_id.md)

Methods

The following methods are supported for the /hierarchyRoots/{ID} resource:

[GET /hierarchyRoots/{ID}](get_hierarchyroots_id.md)

Resource Representation

The /hierarchyRoots/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="HierarchyRootReference" Href="https://localhost:9398/api/hierarchyRoots/0d7ea80c-6ac8-46bf-863c-3a6093f8baec" Name="vcdev51" UID="urn:veeam:HierarchyRoot:0d7ea80c-6ac8-46bf-863c-3a6093f8baec"> |

Entity resource representation:

|  |
| --- |
| <HierarchyRoot xmlns="http://www.veeam.com/ent/v1.0" Type="HierarchyRoot" Href="https://localhost:9398/api/hierarchyRoots/0d7ea80c-6ac8-46bf-863c-3a6093f8baec?format=Entity" Name="vcdev51" UID="urn:veeam:HierarchyRoot:0d7ea80c-6ac8-46bf-863c-3a6093f8baec">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />     <Link Rel="Alternate" Type="HierarchyRootReference" Href="https://localhost:9398/api/hierarchyRoots/0d7ea80c-6ac8-46bf-863c-3a6093f8baec" Name="vc01" />     <Link Rel="Related" Type="ManagedServer" Href="https://localhost:9398/api/managedServers/0d7ea80c-6ac8-46bf-863c-3a6093f8baec?format=Entity" Name="vc01" />   </Links>   <HierarchyRootId>0d7ea80c-6ac8-46bf-863c-3a6093f8baec</HierarchyRootId>   <UniqueId>09D89361-9178-4EAF-8037-E4E82B1932F0</UniqueId>   <HostType>VC</HostType> </HierarchyRoot> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
