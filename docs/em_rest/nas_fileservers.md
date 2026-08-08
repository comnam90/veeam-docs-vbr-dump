---
title: "/nas/fileServers"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/nas_fileservers.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# /nas/fileServers


Represents a collection of all file shares added on backup servers connected to Veeam Backup Enterprise Manager.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/nas/fileServers |

Related Resources

[/nas/fileServers/{ID}](nas_fileservers_id.md)

Methods

The following methods are supported for the /nas/fileServers resource:

[GET /nas/fileServers](get_nas_fileservers.md)

Resource Representation

The /nas/fileServers resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="FileServerReference" Href="https://srv12.tech.local:9398/api/repositories/517be4c8-9c43-4e7c-9f59-4e368d3a8f3c" Name="\\srv12\share" UID="urn:veeam:FileServer:517be4c8-9c43-4e7c-9f59-4e368d3a8f3c">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />       <Link Rel="Alternate" Type="FileServer" Href="https://srv12.tech.local:9398/api/nas/fileServers/517be4c8-9c43-4e7c-9f59-4e368d3a8f3c?format=Entity" Name="\\srv12\share" />     </Links>   </Ref>   <Ref Type="FileServerReference" Href="https://srv12.tech.local:9398/api/repositories/c407ce33-0d08-4aac-8cc0-e28c055ae3bc" Name="172.24.30.115:/home/veeam" UID="urn:veeam:FileServer:c407ce33-0d08-4aac-8cc0-e28c055ae3bc">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />       <Link Rel="Alternate" Type="FileServer" Href="https://srv12.tech.local:9398/api/nas/fileServers/c407ce33-0d08-4aac-8cc0-e28c055ae3bc?format=Entity" Name="172.24.30.115:/home/veeam" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

