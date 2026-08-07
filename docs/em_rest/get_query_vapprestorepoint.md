---
title: "GET /query?type=vAppRestorePoint"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_vapprestorepoint.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=vAppRestorePoint


Returns a resource representation of a collection of vApp restore points created on backup servers that are connected to Veeam Backup Enterprise Manager. For details, see [/vAppRestorePoints](vapprestorepoints.md).

Request

To get a list of vApp restore points, send the GET HTTP request to the query with the type parameter set to vAppRestorePoint.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=vAppRestorePoint |

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
| UID | UidType | UID of the vApp point resource. |
| Name | String | Name of the vApp restore point, for example: vApp02@2025-08-24 05:03:25. |
| CreationTime | DateTime | Date and time when the vApp restore point was created. The parameter accepts only UTC-formatted DateTime values. |
| Type | String | Type of the vApp restore point. Possible values:   * Full * Increment * ReverseIncrement |
| Algorithm | String | Backup method used to create the vApp restore point. Possible values:   * Full * ReversedIncremental * Incremental * SyntheticFull |
| RestorePointId | String | ID of the vApp restore point. |
| VAppDisplayName | String | Display name of the vApp for which the restore point was created. |
| BackupServerUid | UidType | UID of the backup server on which the vApp restore point has been created. |
| BackupServerName | String | Name of the backup server on which the vApp restore point has been created. |

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

In the response body, the REST API returns a representation of the /vAppRestorePoints resource collection.

Example

The example below returns an entity resource representation of a collection of restore points created for vApp vapp001. The results are ordered in the descending order by the CreationTime parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=VAppRestorePoint&format=Entities&sortDesc=CreationTime&filter=VAppDisplayName=="vapp001-98be6b84-236e-4e25-87fe-b0b47fb64764"  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <VAppRestorePoints>       <VAppRestorePoint Type="VAppRestorePoint" Href="https://localhost:9398/api/vAppRestorePoints/e7bc5015-5ecf-4218-9985-ba2d75d9a555?format=Entity" Name="vapp001@2025-06-17 23:56:29" UID="urn:veeam:VAppRestorePoint:e7bc5015-5ecf-4218-9985-ba2d75d9a555" VAppDisplayName="vapp001-98be6b84-236e-4e25-87fe-b0b47fb64764">         <Links>           <Link Rel="Restore" Href="https://localhost:9398/api/vAppRestorePoints/e7bc5015-5ecf-4218-9985-ba2d75d9a555?action=restore" />           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/4d908258-ee9c-4348-8885-ace814008ff4" Name="Jun 17 2025 11:56PM" />           <Link Rel="Alternate" Type="VAppRestorePointReference" Href="https://localhost:9398/api/vAppRestorePoints/e7bc5015-5ecf-4218-9985-ba2d75d9a555" Name="vapp001@2025-06-17 23:56:29" />         </Links>         <CreationTimeUTC>2025-06-17T23:56:29.653Z</CreationTimeUTC>         <Algorithm>Incremental</Algorithm>         <PointType>Increment</PointType>         <HierarchyObjRef>urn:vCloud:Vapp:5d25f98b-90fb-452c-92a7-58e52adf2ed3.urn:vcloud:vapp:1ef16c93-4cc8-4d88-a978-076bb3254ab1</HierarchyObjRef>       </VAppRestorePoint>       <VAppRestorePoint Type="VAppRestorePoint" Href="https://localhost:9398/api/vAppRestorePoints/b3852cb8-b5e0-4300-8783-1732c97819a1?format=Entity" Name="vapp001@2025-06-05 01:01:50" UID="urn:veeam:VAppRestorePoint:b3852cb8-b5e0-4300-8783-1732c97819a1" VAppDisplayName="vapp001">         <Links>           <Link Rel="Restore" Href="https://localhost:9398/api/vAppRestorePoints/b3852cb8-b5e0-4300-8783-1732c97819a1?action=restore" />           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/f22db071-39ba-4ca5-a492-0a451c0299d7" Name="Jun  5 2025  1:01AM" />           <Link Rel="Alternate" Type="VAppRestorePointReference" Href="https://localhost:9398/api/vAppRestorePoints/b3852cb8-b5e0-4300-8783-1732c97819a1" Name="vapp001@2025-06-05 01:01:50" />         </Links>         <CreationTimeUTC>2025-06-05T01:01:50.997Z</CreationTimeUTC>         <Algorithm>Full</Algorithm>         <PointType>Full</PointType>         <HierarchyObjRef>urn:vCloud:Vapp:5d25f98b-90fb-452c-92a7-58e52adf2ed3.urn:vcloud:vapp:1ef16c93-4cc8-4d88-a978-076bb3254ab1</HierarchyObjRef>       </VAppRestorePoint>       <VAppRestorePoint Type="VAppRestorePoint" Href="https://localhost:9398/api/vAppRestorePoints/ae418609-22a3-47e7-813a-0d6bfbf0ca01?format=Entity" Name="vapp001@2025-05-27 12:56:22" UID="urn:veeam:VAppRestorePoint:ae418609-22a3-47e7-813a-0d6bfbf0ca01" VAppDisplayName="vapp001">         <Links>           <Link Rel="Restore" Href="https://localhost:9398/api/vAppRestorePoints/ae418609-22a3-47e7-813a-0d6bfbf0ca01?action=restore" />           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/f63e44bf-28f2-4a6c-a041-dc9afc9bc785" Name="May 27 2025 12:55PM" />           <Link Rel="Alternate" Type="VAppRestorePointReference" Href="https://localhost:9398/api/vAppRestorePoints/ae418609-22a3-47e7-813a-0d6bfbf0ca01" Name="vapp001@2025-05-27 12:56:22" />         </Links>         <CreationTimeUTC>2025-05-27T12:56:22.377Z</CreationTimeUTC>         <Algorithm>Full</Algorithm>         <PointType>Full</PointType>         <HierarchyObjRef>urn:vCloud:Vapp:5d25f98b-90fb-452c-92a7-58e52adf2ed3.urn:vcloud:vapp:1ef16c93-4cc8-4d88-a978-076bb3254ab1</HierarchyObjRef>       </VAppRestorePoint>     </VAppRestorePoints>   </Entities>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=VAppRestorePoint&format=Entities&sortDesc=CreationTime&filter=VAppDisplayName=="vapp001"&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=VAppRestorePoint&format=Entities&sortDesc=CreationTime&filter=VAppDisplayName=="vapp001"&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

