---
title: "GET /query?type=RestorePoint"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_restorepoint.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=RestorePoint


Returns a resource representation of a restore points collection for backups and replicas created on or imported to backup servers connected to Veeam Backup Enterprise Manager. For details, see [/restorePoints](restorepoints.md).

Request

To get a list of restore points, send the GET HTTP request to the query with the type parameter set to RestorePoint.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=RestorePoint |

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
| UID | UidType | UID of the restore point resource, for example: urn:veeam:RestorePoint:bf0542a7-baea-41fa-baec-12e76043d0e1 |
| Name | String | Name of the restore point, for example: Aug 26 2025 7:57AM. |
| CreationTime | DateTime | Date and time when the restore point was created. The parameter accepts only UTC-formatted DateTime values. |
| BackupUid | UidType | UID of the VM backup parent to the restore point resource. |
| BackupName | String | Name of the backup parent to the restore point resource. |
| BackupServerUid | UidType | UID of the backup server on which the restore point has been created. |
| BackupServerName | String | Name of the backup server on which the restore point has been created. |

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

In the response body, the REST API returns a representation of the /restorePoints resource collection.

Example

The example below returns an entity resource representation of a collection of restore points for the backup with name Backup Job 5. The results are ordered in the acceding order by the Name parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=RestorePoint&format=Entities&sortAsc=name&filter=BackupName=="Backup Job 5"  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <RestorePoints>       <RestorePoint Type="RestorePoint" Href="https://localhost:9398/api/restorePoints/f22db071-39ba-4ca5-a492-0a451c0299d7?format=Entity" Name="Jun  5 2025  1:01AM" UID="urn:veeam:RestorePoint:f22db071-39ba-4ca5-a492-0a451c0299d7">         <Links>           <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/d9470b6c-d64e-477b-a813-ae9dde7791f5" Name="Backup Job 5" />           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Alternate" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/f22db071-39ba-4ca5-a492-0a451c0299d7" Name="Jun  5 2025  1:01AM" />           <Link Rel="Down" Type="VAppRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/f22db071-39ba-4ca5-a492-0a451c0299d7/vAppRestorePoints" />           <Link Rel="Related" Type="BackupFileReferenceList" Href="https://localhost:9398/api/restorePoints/f22db071-39ba-4ca5-a492-0a451c0299d7/backupFiles" />         </Links>         <BackupDateUTC>2025-06-05T01:01:27.11Z</BackupDateUTC>       </RestorePoint>       <RestorePoint Type="RestorePoint" Href="https://localhost:9398/api/restorePoints/f63e44bf-28f2-4a6c-a041-dc9afc9bc785?format=Entity" Name="May 27 2025 12:55PM" UID="urn:veeam:RestorePoint:f63e44bf-28f2-4a6c-a041-dc9afc9bc785">         <Links>           <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/d9470b6c-d64e-477b-a813-ae9dde7791f5" Name="Backup Job 5" />           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Alternate" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/f63e44bf-28f2-4a6c-a041-dc9afc9bc785" Name="May 27 2025 12:55PM" />           <Link Rel="Down" Type="VAppRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/f63e44bf-28f2-4a6c-a041-dc9afc9bc785/vAppRestorePoints" />           <Link Rel="Related" Type="BackupFileReferenceList" Href="https://localhost:9398/api/restorePoints/f63e44bf-28f2-4a6c-a041-dc9afc9bc785/backupFiles" />         </Links>         <BackupDateUTC>2025-05-27T12:55:57.45Z</BackupDateUTC>       </RestorePoint>     </RestorePoints>   </Entities>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=RestorePoint&format=Entities&sortAsc=name&filter=BackupName=="Backup+Job+5"&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=RestorePoint&format=Entities&sortAsc=name&filter=BackupName=="Backup+Job+5"&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

