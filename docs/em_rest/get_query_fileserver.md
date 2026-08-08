---
title: "GET /query?type=FileServer"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_fileserver.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=FileServer


Returns a resource representation of a collection of file shares added on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/nas/fileServers](nas_fileservers.md).

Request

To get a list of file shares, send the GET HTTP request to the query with the type parameter set to FileServer.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=FileServer |

Request Headers

The request contains the following headers:

Request Headers

| Header | Required | Description |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Optional Parameters

In the query, you can use the following parameters for filtering and sorting.

Optional Parameters

| Parameter | Type | Description |
| UID | UidType | UID of the file share, for example: urn:veeam:FileServer:517be4c8-9c43-4e7c-9f59-4e368d3a8f3c. |
| Name | String | Name of the file share, for example: \\srv12\share. |
| BackupServerUid | UidType | UID of the backup server parent to the file share resource. |
| BackupServerName | String | Name of the backup server parent to the file share resource. |

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 200 OK.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

Response Headers

| Header | Description |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns a representation of the /nas/fileServers resource collection.

Example

The example below returns an entity resource representation of a collection of file shares added on the backup server with name enterprise06.tech.local. The results are ordered in the acceding order by the Name parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=FileServer&format=Entities&sortAsc=name&filter=BackupServerName=="enterprise06.tech.local"  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <FileServers>       <FileServer Type="FileServer" Href="https://localhost:9398/api/nas/fileServers/f5d9ea1f-ef70-4e51-af3d-c760380d5347?format=Entity" Name="enterprise04.tech.local" UID="urn:veeam:FileServer:f5d9ea1f-ef70-4e51-af3d-c760380d5347">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Alternate" Type="FileServerReference" Href="https://localhost:9398/api/nas/fileServers/f5d9ea1f-ef70-4e51-af3d-c760380d5347" Name="enterprise04.tech.local" />         </Links>         <ServerType>FileServer</ServerType>         <HierarchyObjRef>urn:NasBackup:FileServer:ee50f2fb-034f-41cd-8dc8-904aeae2d0d8.f5d9ea1f-ef70-4e51-af3d-c760380d5347</HierarchyObjRef>         <FileServerOptions>           <ServerUid>urn:veeam:FileServer:f5d9ea1f-ef70-4e51-af3d-c760380d5347</ServerUid>         </FileServerOptions>         <ProcessingOptions>           <ServerUid>urn:veeam:FileServer:f5d9ea1f-ef70-4e51-af3d-c760380d5347</ServerUid>           <CacheRepositoryUid>urn:veeam:Repository:d4b5e196-f3ad-474c-99bc-dfef051dae07</CacheRepositoryUid>         </ProcessingOptions>         <NASServerAdvancedOptions>           <ProcessingMode>Direct</ProcessingMode>         </NASServerAdvancedOptions>       </FileServer>       <FileServer Type="FileServer" Href="https://localhost:9398/api/nas/fileServers/1131bc00-36c0-4355-87fc-7f748aceb978?format=Entity" Name="winsrv88.tech.local:/nfs\_share" UID="urn:veeam:FileServer:1131bc00-36c0-4355-87fc-7f748aceb978">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Alternate" Type="FileServerReference" Href="https://localhost:9398/api/nas/fileServers/1131bc00-36c0-4355-87fc-7f748aceb978" Name="winsrv88.tech.local:/nfs\_share" />         </Links>         <ServerType>NfsServer</ServerType>         <HierarchyObjRef>urn:NasBackup:FileServer:35ab6523-0e40-4d92-a0ea-11465791cd91.1131bc00-36c0-4355-87fc-7f748aceb978</HierarchyObjRef>         <NfsServerOptions>           <Path>winsrv88.tech.local:/nfs\_share</Path>         </NfsServerOptions>         <ProcessingOptions>           <ServerUid>urn:veeam:FileServer:1131bc00-36c0-4355-87fc-7f748aceb978</ServerUid>           <CacheRepositoryUid>urn:veeam:Repository:88788f9e-d8f5-4eb4-bc4f-9b3f5403bcec</CacheRepositoryUid>         </ProcessingOptions>         <NASServerAdvancedOptions>           <ProcessingMode>Direct</ProcessingMode>         </NASServerAdvancedOptions>       </FileServer>     </FileServers>   </Entities>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=FileServer&format=Entities&sortAsc=name&filter=BackupServerName=="enterprise06.tech.local"&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=FileServer&format=Entities&sortAsc=name&filter=BackupServerName=="enterprise06.tech.local"&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

