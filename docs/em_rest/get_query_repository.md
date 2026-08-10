---
title: "GET /query?type=Repository"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_repository.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=Repository


Returns a resource representation of the collection of backup repositories created on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/repositories](repositories.md).

Request

To get a list of repositories, send the GET HTTP request to the query with the type parameter set to Repository.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=Repository |

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
| UID | UidType | UID of the backup repository resource, for example: urn: veeam:Repository:b609c947-dd30-4295-8b57-cc880329dbd6. |
| Name | String | Name of the backup repository, for example: Backups Vol2. |
| FreeSpace | Int64 | Free space available on the backup repository. |
| Capacity | Int64 | Total space available on the backup repository. |
| BackupServerUid | UidType | UID of the backup server parent to the backup repository resource, for example: urn:veeam:BackupServer:15942270-fb56-4dcc-96e9-5f80e4725a15. |
| BackupServerName | String | Name of the backup server parent to the backup repository resource. for example: BACKUPSERVER. |

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

In the response body, the REST API returns a representation of the /repositories resource collection.

Example

The example below returns an entity resource representation of a collection of backup repositories that have less than 100 GB of free space.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=Repository&format=Entities&filter=FreeSpace<107374182400  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <Repositories>       <Repository Type="Repository" Href="https://localhost:9398/api/repositories/425b6739-5082-4f7a-99fb-1ae13ef87d9f?format=Entity" Name="Default Backup Repository" UID="urn:veeam:Repository:425b6739-5082-4f7a-99fb-1ae13ef87d9f">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Alternate" Type="RepositoryReference" Href="https://localhost:9398/api/repositories/425b6739-5082-4f7a-99fb-1ae13ef87d9f" Name="Default Backup Repository" />           <Link Rel="Down" Type="BackupReferenceList" Href="https://localhost:9398/api/repositories/425b6739-5082-4f7a-99fb-1ae13ef87d9f/backups" />           <Link Rel="Down" Type="ReplicaReferenceList" Href="https://localhost:9398/api/repositories/425b6739-5082-4f7a-99fb-1ae13ef87d9f/replicas" />         </Links>         <Capacity>106779635712</Capacity>         <FreeSpace>9223929856</FreeSpace>         <Kind>WindowsLocal</Kind>       </Repository>       <Repository Type="Repository" Href="https://localhost:9398/api/repositories/af17b1f7-71ca-4664-ac70-9676b80d127f?format=Entity" Name="Default Backup Repository" UID="urn:veeam:Repository:af17b1f7-71ca-4664-ac70-9676b80d127f">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/beda8585-1354-451c-afe2-646dcf42afa6" Name="backupsrv29.tech.local" />           <Link Rel="Alternate" Type="RepositoryReference" Href="https://localhost:9398/api/repositories/af17b1f7-71ca-4664-ac70-9676b80d127f" Name="Default Backup Repository" />           <Link Rel="Down" Type="BackupReferenceList" Href="https://localhost:9398/api/repositories/af17b1f7-71ca-4664-ac70-9676b80d127f/backups" />           <Link Rel="Down" Type="ReplicaReferenceList" Href="https://localhost:9398/api/repositories/af17b1f7-71ca-4664-ac70-9676b80d127f/replicas" />         </Links>         <Capacity>128479916032</Capacity>         <FreeSpace>88319569920</FreeSpace>         <Kind>WindowsLocal</Kind>       </Repository>     </Repositories>   </Entities>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=Repository&format=Entities&filter=FreeSpace>107374182400&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=Repository&format=Entities&filter=FreeSpace>107374182400&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

