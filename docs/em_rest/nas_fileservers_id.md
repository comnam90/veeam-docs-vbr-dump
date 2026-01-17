---
title: "/nas/fileServers/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/nas_fileservers_id.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /nas/fileServers/{ID}


Represents a file share having the specified ID. The file share is added on a backup server connected to Veeam Backup Enterprise Manager.

Resource URL

The URL of the reference resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/nas/fileServers/{ID} |

The URL of the entity resource representation:

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/nas/fileServers/{ID}?format=Entity |

Related Resources

[/backupServers/{ID}](backupservers_id.md)

Methods

The following methods are supported for the /nas/fileServers/{ID} resource:

[GET /nas/fileServers/{ID}](get_nas_fileservers_id.md)

Resource Representation

The /nas/fileServers/{ID} resource has a resource representation of the following types.

Entity reference resource representation:

|  |
| --- |
| <EntityRef xmlns="http://www.veeam.com/ent/v1.0" Type="FileServerReference" Href="https://srv12.tech.local:9398/api/repositories/517be4c8-9c43-4e7c-9f59-4e368d3a8f3c" Name="\\srv12\share" UID="urn:veeam:FileServer:517be4c8-9c43-4e7c-9f59-4e368d3a8f3c"> |

Entity resource representation:

|  |
| --- |
| <FileServer xmlns="http://www.veeam.com/ent/v1.0" Type="FileServer" Href="https://srv12.tech.local:9398/api/nas/fileServers/517be4c8-9c43-4e7c-9f59-4e368d3a8f3c?format=Entity" Name="\\srv12\share" UID="urn:veeam:FileServer:517be4c8-9c43-4e7c-9f59-4e368d3a8f3c">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />     <Link Rel="Alternate" Type="FileServerReference" Href="https://srv12.tech.local:9398/api/nas/fileServers/517be4c8-9c43-4e7c-9f59-4e368d3a8f3c" Name="\\srv12\share" />   </Links>   <ServerType>SmbServer</ServerType>   <HierarchyObjRef>urn:NasBackup:FileServer:5735d1af-3aad-49ac-ac77-eab708ac1a37.517be4c8-9c43-4e7c-9f59-4e368d3a8f3c</HierarchyObjRef>   <SmbServerOptions>     <Path>\\srv12\share</Path>     <CredentialsId>43f9521d-7b9a-4be5-847f-fd69cf19bded</CredentialsId>   </SmbServerOptions>   <ProcessingOptions>     <ServerUid>urn:veeam:FileServer:517be4c8-9c43-4e7c-9f59-4e368d3a8f3c</ServerUid>     <CacheRepositoryUid>urn:veeam:Repository:88788f9e-d8f5-4eb4-bc4f-9b3f5403bcec</CacheRepositoryUid>   </ProcessingOptions>   <NASServerAdvancedOptions>     <ProcessingMode>Direct</ProcessingMode>   </NASServerAdvancedOptions> </FileServer> |


