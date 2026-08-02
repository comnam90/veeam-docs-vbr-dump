---
title: "/managedServers"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/managedservers.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /managedServers


Represents a collection of servers connected to backup servers that are managed by Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/managedServers |

Related Resources

* [/hierarchyRoots](hierarchyroots.md)
* [/managedServers/{ID}](managedservers_id.md)

Methods

The following methods are supported for the /managedServers resource:

[GET /managedServers](get_managedservers.md)

Resource Representation

The /managedServers resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="ManagedServerReference" Href="https://localhost:9398/api/managedServers/0d7ea80c-6ac8-46bf-863c-3a6093f8baec" Name="vc01" UID="urn:veeam:ManagedServer:0d7ea80c-6ac8-46bf-863c-3a6093f8baec">     <Links>       <Link Rel="Alternate" Type="ManagedServer" Href="https://localhost:9398/api/managedServers/0d7ea80c-6ac8-46bf-863c-3a6093f8baec?format=Entity" Name="vc01" />       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02" />     </Links>   </Ref>   <Ref Type="ManagedServerReference" Href="https://localhost:9398/api/managedServers/a5352877-3b99-4e2a-8700-400cb3eefb56" Name="172.16.16.77" UID="urn:veeam:ManagedServer:a5352877-3b99-4e2a-8700-400cb3eefb56">     <Links>       <Link Rel="Alternate" Type="ManagedServer" Href="https://localhost:9398/api/managedServers/a5352877-3b99-4e2a-8700-400cb3eefb56?format=Entity" Name="172.16.16.77" />       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02" />     </Links>   </Ref>   <Ref Type="ManagedServerReference" Href="https://localhost:9398/api/managedServers/5b133853-b0cf-4bb6-8c11-4f9dcb258b26" Name="172.16.13.45" UID="urn:veeam:ManagedServer:5b133853-b0cf-4bb6-8c11-4f9dcb258b26">     <Links>       <Link Rel="Alternate" Type="ManagedServer" Href="https://localhost:9398/api/managedServers/5b133853-b0cf-4bb6-8c11-4f9dcb258b26?format=Entity" Name="172.16.13.45" />       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02" />     </Links>   </Ref>   <Ref Type="ManagedServerReference" Href="https://localhost:9398/api/managedServers/5b768a76-bcc1-48ed-af47-85424cc43584" Name="172.16.1.102" UID="urn:veeam:ManagedServer:5b768a76-bcc1-48ed-af47-85424cc43584">     <Links>       <Link Rel="Alternate" Type="ManagedServer" Href="https://localhost:9398/api/managedServers/5b768a76-bcc1-48ed-af47-85424cc43584?format=Entity" Name="172.16.1.102" />       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02" />     </Links>   </Ref>  </EntityReferences> |

Page updated 2026-07-29

