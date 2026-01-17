---
title: "/managedServers/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/managedservers_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a server having the specified ID.

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/managedServers/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/managedServers/{ID}?format=Entity |

Related Resources

[/hierarchyRoots/{ID}](hierarchyroots_id.md)

Methods

The following methods are supported for the /managedServers/{ID} resource:

[GET /managedServers/{ID}](get_managedservers_id.md)

Resource Representation

The /managedServers/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="ManagedServerReference" Href="https://localhost:9398/api/managedServers/a5352877-3b99-4e2a-8700-400cb3eefb56" Name="172.16.16.77" UID="urn:veeam:ManagedServer:a5352877-3b99-4e2a-8700-400cb3eefb56"> |

Entity resource representation:

|  |
| --- |
| <ManagedServer xmlns="http://www.veeam.com/ent/v1.0" Type="ManagedServer" Href="https://localhost:9398/api/managedServers/a5352877-3b99-4e2a-8700-400cb3eefb56?format=Entity" Name="172.16.16.77" UID="urn:veeam:ManagedServer:a5352877-3b99-4e2a-8700-400cb3eefb56">   <Links>     <Link Rel="Up" Type="BackupServer" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018?format=Entity" Name="srv02.tech.local" />     <Link Rel="Alternate" Type="ManagedServerReference" Href="https://localhost:9398/api/managedServers/a5352877-3b99-4e2a-8700-400cb3eefb56" Name="172.16.16.77" />     <Link Rel="Related" Type="HierarchyRoot" Href="https://localhost:9398/api/hierarchyRoots/a5352877-3b99-4e2a-8700-400cb3eefb56?format=Entity" Name="172.16.16.77" />   </Links>   <Description>Target Windows server.</Description>   <ManagedServerType>Windows</ManagedServerType> </ManagedServer> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
