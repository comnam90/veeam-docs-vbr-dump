---
title: "GET /query?type=BackupFile"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_backupfile.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=BackupFile


Returns a resource representation of a collection of backup files created on or imported to backup servers connected to Veeam Backup Enterprise Manager. For details, see [/backupFiles](backupfiles.md).

Request

To get a list of backup files, send the GET HTTP request to the query with the type parameter set to BackupFile.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=BackupFile |

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
| UID | UidType | UID of the backup file resource, for example: urn:veeam:BackupFile:0874ab95-10e5-4f25-84df-2782ad81f3e5. |
| Name | String | Name of the backup file, for example: Webserver BackupD2025-09-20T175902.vib. |
| CreationTimeUTC | DateTime | Date and time when the backup file was created. The parameter accepts only UTC-formatted DateTime values. |
| BackupSize | Long | Size of the backup file (in bytes). |
| DataSize | Long | Size of the backed-up data (in bytes). |
| CompressRatio | Double | Data compression ratio. |
| FileType | String | Type of the backup file. Possible values:   * vbk * vib * vrb |
| BackupUid | UidType | UID of the VM backup parent to the backup file resource. |
| BackupName | String | Name of the backup parent to the backup file resource. |
| BackupServerUid | UidType | UID of the backup server parent to the backup file resource. |
| BackupServerName | String | Name of the backup server parent to the backup file resource. |

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

In the response body, the REST API returns a representation of the /backupFiles resource collection.

Example

The example below returns an entity resource representation of a collection of VBK backup files contained in the backup that have ID 39cb6675-8930-436a-8ac3-8a4ae6195cb1.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=BackupFile&format=Entities&filter=BackupUid=="urn:veeam:Backup:39cb6675-8930-436a-8ac3-8a4ae6195cb1";FileType==vbk  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <BackupFiles>       <BackupFile Type="BackupFile" Href="https://localhost:9398/api/backupFiles/77c68f2e-fd26-4eba-9d69-74103cbb3911?format=Entity" Name="Backup Job 1D2025-05-29T060108\_8D1C.vbk" UID="urn:veeam:BackupFile:77c68f2e-fd26-4eba-9d69-74103cbb3911">         <Links>           <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/39cb6675-8930-436a-8ac3-8a4ae6195cb1" Name="Backup Job 1" />           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Alternate" Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/77c68f2e-fd26-4eba-9d69-74103cbb3911" Name="Backup Job 1D2025-05-29T060108\_8D1C.vbk" />           <Link Rel="Related" Type="RestorePointReferenceList" Href="https://localhost:9398/api/backupFiles/77c68f2e-fd26-4eba-9d69-74103cbb3911/restorePoints" />           <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/backupFiles/77c68f2e-fd26-4eba-9d69-74103cbb3911/vmRestorePoints" />         </Links>         <FilePath>C:\Backup\Backup Job 1\Backup Job 1D2025-05-29T060108\_8D1C.vbk</FilePath>         <BackupSize>8682549248</BackupSize>         <DataSize>75161991659</DataSize>         <DeduplicationRatio>5.71</DeduplicationRatio>         <CompressRatio>1.52</CompressRatio>         <CreationTimeUtc>2025-05-29T04:00:20.32Z</CreationTimeUtc>         <FileType>vbk</FileType>       </BackupFile>     </BackupFiles>   </Entities>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=BackupFile&format=Entities&sortAsc=name&filter=BackupUid=="urn:veeam:Backup:39cb6675-8930-436a-8ac3-8a4ae6195cb1";FileType==vbk&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=BackupFile&format=Entities&sortAsc=name&filter=BackupUid=="urn:veeam:Backup:39cb6675-8930-436a-8ac3-8a4ae6195cb1";FileType==vbk&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-28

