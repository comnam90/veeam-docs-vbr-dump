---
title: "GET /query?type=NasObject"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_nasobject.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=NasObject


Returns a list of files and folders processed by file share backup jobs. For details, see [/nas/jobs/{ID}/includes](nas_jobs_id_includes.md).

Request

To get a list of files and folders processed by file share backup jobs, send the GET HTTP request to the query with the type parameter set to NasObject.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=NasObject |

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
| UID | String | ID of the file or folder processed by the job, for example: 6fefb504-856d-4c31-b767-76af5567c407. |
| Name | String | Name of the file or folder processed by the job, for example: \\srv12\share\archive. |
| JobUid | UidType | UID of the file share backup job parent to the file or folder resource, for example: urn:veeam:Job:da736815-4fea-4c8e-b0e1-5ecdbca1c512. |
| JobName | String | Name of the file share backup job parent to the file or folder resource, for example: Shared Files Backup. |
| FileServerUid | UidType | UID of the file share parent to the file or folder resource, for example: urn:veeam:FileServer:517be4c8-9c43-4e7c-9f59-4e368d3a8f3c. |
| FileServerName | String | Name of the file share parent to the file or folder resource, for example: \\srv12\share. |
| BackupServerUid | UidType | UID of the backup server on which the file share parent to the file or folder resource is added, for example: urn:veeam:BackupServer:15942270-fb56-4dcc-96e9-5f80e4725a15. |
| BackupServerName | String | Name of the backup server on which the file share parent to the file or folder resource is added, for example: srv01. |

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

In the response body, the REST API returns a representation of the /nas/jobs/{ID}/includes resource collection.

Example

The example below returns an entity resource representation of a collection of files and folders processed by file share backup jobs created on the enterprise06.tech.local backup server. The results are ordered in the acceding order by the JobName parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=NasObject&format=Entities&sortAsc=JobName&filter=BackupServerName=="enterprise06.tech.local"  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Resources>     <NASObjects>       <NASObject Type="NasObject" Href="https://localhost:9398/api/nas/jobs/e72c6fce-0680-4340-896f-e44903677ade/includes/f33fe405-a460-415e-9ffc-d1ef2e0b6c03">         <Links>           <Link Rel="Up" Type="Job" Href="https://localhost:9398/api/nas/jobs/e72c6fce-0680-4340-896f-e44903677ade?format=Entity" Name="File Backup Job 1" />           <Link Rel="Related" Type="FileServer" Href="https://localhost:9398/api/nas/fileServers/1131bc00-36c0-4355-87fc-7f748aceb978?format=Entity" Name="winsrv88.tech.local:/nfs\_share" />         </Links>         <HierarchyObjRef>urn:NasBackup:BackupServer:35ab6523-0e40-4d92-a0ea-11465791cd91</HierarchyObjRef>         <ObjectInJobId>f33fe405-a460-415e-9ffc-d1ef2e0b6c03</ObjectInJobId>         <FileOrFolder>winsrv88.tech.local:/nfs\_share</FileOrFolder>         <FileServerUid>urn:veeam:FileServer:1131bc00-36c0-4355-87fc-7f748aceb978</FileServerUid>         <InclusionMask>           <Extension>\*.\*</Extension>         </InclusionMask>       </NASObject>       <NASObject Type="NasObject" Href="https://localhost:9398/api/nas/jobs/0700a278-3d73-4584-a8cf-104b48e0c98c/includes/a8c6797f-ab9e-4f06-9656-60d17a4f0672">         <Links>           <Link Rel="Up" Type="Job" Href="https://localhost:9398/api/nas/jobs/0700a278-3d73-4584-a8cf-104b48e0c98c?format=Entity" Name="File Backup Job 2" />           <Link Rel="Related" Type="FileServer" Href="https://localhost:9398/api/nas/fileServers/f5d9ea1f-ef70-4e51-af3d-c760380d5347?format=Entity" Name="enterprise04.tech.local" />         </Links>         <HierarchyObjRef>urn:NasBackup:FileServer:ee50f2fb-034f-41cd-8dc8-904aeae2d0d8</HierarchyObjRef>         <ObjectInJobId>a8c6797f-ab9e-4f06-9656-60d17a4f0672</ObjectInJobId>         <FileOrFolder>C:\File Share</FileOrFolder>         <FileServerUid>urn:veeam:FileServer:f5d9ea1f-ef70-4e51-af3d-c760380d5347</FileServerUid>         <InclusionMask>           <Extension>\*.\*</Extension>         </InclusionMask>       </NASObject>     </NASObjects>   </Resources>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=NasObject&format=Entities&sortAsc=JobName&filter=BackupServerName=="enterprise06.tech.local"&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=NasObject&format=Entities&sortAsc=JobName&filter=BackupServerName=="enterprise06.tech.local"&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

