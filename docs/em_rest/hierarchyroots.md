---
title: "/hierarchyRoots"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/hierarchyroots.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /hierarchyRoots


Represents a collection of all virtualization hosts added to the backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/hierarchyRoots |

Related Resources

* [/managedServers](managedservers.md)
* [/hierarchyRoots/{ID}](hierarchyroots_id.md)

Methods

The following methods are supported for the /hierarchyRoots resource:

[GET /hierarchyRoots](get_hierarchyroots.md)

Resource Representation

The /hierarchyRoots resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="HierarchyRootReference" Href="https://localhost:9398/api/hierarchyRoots/0d7ea80c-6ac8-46bf-863c-3a6093f8baec" Name="vc01" UID="urn:veeam:HierarchyRoot:0d7ea80c-6ac8-46bf-863c-3a6093f8baec">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="HierarchyRoot" Href="https://localhost:9398/api/hierarchyRoots/0d7ea80c-6ac8-46bf-863c-3a6093f8baec?format=Entity" Name="vcdev51" />     </Links>   </Ref>   <Ref Type="HierarchyRootReference" Href="https://localhost:9398/api/hierarchyRoots/15410946-fc21-4b82-a53a-717478eae90f" Name="172.16.13.45" UID="urn:veeam:HierarchyRoot:15410946-fc21-4b82-a53a-717478eae90f">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="HierarchyRoot" Href="https://localhost:9398/api/hierarchyRoots/15410946-fc21-4b82-a53a-717478eae90f?format=Entity" Name="172.16.13.45" />     </Links>   </Ref>   <Ref Type="HierarchyRootReference" Href="https://localhost:9398/api/hierarchyRoots/9f591b3b-0072-4326-9bcc-9dabb4218df5" Name="172.16.21.1" UID="urn:veeam:HierarchyRoot:9f591b3b-0072-4326-9bcc-9dabb4218df5">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="HierarchyRoot" Href="https://localhost:9398/api/hierarchyRoots/9f591b3b-0072-4326-9bcc-9dabb4218df5?format=Entity" Name="172.16.21.1" />     </Links>   </Ref>   <Ref Type="HierarchyRootReference" Href="https://localhost:9398/api/hierarchyRoots/d63a6e79-e771-4c77-80be-ad7b6edc2ba7" Name="172.16.1.57" UID="urn:veeam:HierarchyRoot:d63a6e79-e771-4c77-80be-ad7b6edc2ba7">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="HierarchyRoot" Href="https://localhost:9398/api/hierarchyRoots/d63a6e79-e771-4c77-80be-ad7b6edc2ba7?format=Entity" Name="172.16.1.57" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

