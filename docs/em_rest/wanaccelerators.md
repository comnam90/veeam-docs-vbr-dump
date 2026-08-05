---
title: "/wanAccelerators"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/wanaccelerators.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /wanAccelerators


Represents a collection of WAN accelerators configured on all backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/wanAccelerators |

Related Resources

[/wanAccelerators/{ID}](wanaccelerators_id.md)

Methods

The following methods are supported for the /wanAccelerators resource:

[GET /wanAccelerators](get_wanaccelerators.md)

Resource Representation

The /wanAccelerators resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="WanAcceleratorReference" Href="https://localhost:9398/api/wanAccelerators/55bd11af-696d-4224-ae9c-0917c851177c" Name="172.16.13.45" UID="urn:veeam:WanAccelerator:55bd11af-696d-4224-ae9c-0917c851177c">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="WanAccelerator" Href="https://localhost:9398/api/wanAccelerators/55bd11af-696d-4224-ae9c-0917c851177c?format=Entity" Name="172.16.13.45" />     </Links>   </Ref>   <Ref Type="WanAcceleratorReference" Href="https://localhost:9398/api/wanAccelerators/b1752038-f542-42a8-aec0-15bf3f4b15c8" Name="172.16.16.77" UID="urn:veeam:WanAccelerator:b1752038-f542-42a8-aec0-15bf3f4b15c8">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="WanAccelerator" Href="https://localhost:9398/api/wanAccelerators/b1752038-f542-42a8-aec0-15bf3f4b15c8?format=Entity" Name="172.16.16.77" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

