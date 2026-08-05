---
title: "GET /query?type=vAppReplicaPoint"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_vappreplicapoint.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=vAppReplicaPoint


Returns resource representation of a collection of restore points of separate vApps replicas. For details, see [/vAppReplicaPoints](vappreplicapoints.md).

Request

To get a list of restore points of separate vApps replicas, send the GET HTTP request to the query with the type parameter set to vAppReplicaPoint.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=vAppReplicaPoint |

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
| UID | UidType | UID of the vApp replica point resource. |
| Name | String | Name of the vApp replica point, for example: vApp01@2025-02-04 00:08:35. |
| vAppDisplayName | String | Display name of the vApp for which the restore point has been created. |
| CreationTime | DateTime | Date and time when the restore point was created. The parameter accepts only UTC-formatted DateTime values. |
| vAppName | String | Name of the vApp for which the restore point has been created. |
| Type | String | Type of the vApp replica point. Possible values:   * Full * ReverseIncrement * Increment * Snapshot |
| Algorithm | String | Replication method used to create the restore point. Possible values:   * Full * ReversedIncremental * Incremental * SyntheticFull |
| ReplicaUid | UidType | UID of the vApp replica parent to the vApp replica point resource. |
| ReplicaName | String | Name of the vApp replica parent to the vApp replica point resource. |
| BackupServerUid | UidType | UID of the backup server where the vApp replica restore point has been created. |
| BackupServerName | String | Name of the backup server where the vApp replica restore point has been created. |

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

In the response body, the REST API returns a representation of the /vAppReplicaPoints resource collection.

Example

The example below returns a list of vApp replica restore points created on backup servers connected to Veeam Backup Enterprise Manager

The example below returns an entity resource representation of a collection of vApp replica restore points created for vApp vApp002. The results are ordered in the descending order by the CreationTime parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=VAppReplicaPoint&format=Entities&sortDesc=CreationTime&filter=VAppName==vApp002  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <VAppReplicaPoints>       <VAppReplicaPoint Type="VAppReplicaPoint" Href="https://localhost:9398/api/vAppReplicaPoints/7ba40ff8-2fd2-49e8-9c14-831f6e8203ca?format=Entity" Name="vApp002@2025-06-18 10:36:45" UID="urn:veeam:VAppReplicaPoint:7ba40ff8-2fd2-49e8-9c14-831f6e8203ca" VAppDisplayName="vApp002">         <Links>           <Link Rel="Failover" Href="https://localhost:9398/api/vAppReplicaPoints/7ba40ff8-2fd2-49e8-9c14-831f6e8203ca?action=failover" />           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Up" Type="ReplicaReference" Href="https://localhost:9398/api/replicas/057050bf-072e-4ed4-8130-2af1ccee6c1a" Name="Replication Job 3" />           <Link Rel="Alternate" Type="VAppReplicaPointReference" Href="https://localhost:9398/api/vAppReplicaPoints/7ba40ff8-2fd2-49e8-9c14-831f6e8203ca" Name="vApp002@2025-06-18 10:36:45" />           <Link Rel="Down" Type="VmReplicaPointReference" Href="https://localhost:9398/api/vmReplicaPoints/55b150fd-4cde-4a62-97d3-8a52e51f51e6" Name="AnT\_VM1-Rtnu@2025-06-18 10:36:45" />         </Links>         <CreationTimeUTC>2025-06-18T10:36:45.317Z</CreationTimeUTC>         <VAppName>vApp002</VAppName>         <Algorithm>Full</Algorithm>         <PointType>Snapshot</PointType>       </VAppReplicaPoint>       <VAppReplicaPoint Type="VAppReplicaPoint" Href="https://localhost:9398/api/vAppReplicaPoints/7ba40ff8-2fd2-49e8-9c14-831f6e8203ca?format=Entity" Name="vApp002@2025-06-18 10:36:45" UID="urn:veeam:VAppReplicaPoint:7ba40ff8-2fd2-49e8-9c14-831f6e8203ca" VAppDisplayName="vApp002">         <Links>           <Link Rel="Failover" Href="https://localhost:9398/api/vAppReplicaPoints/7ba40ff8-2fd2-49e8-9c14-831f6e8203ca?action=failover" />           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Up" Type="ReplicaReference" Href="https://localhost:9398/api/replicas/057050bf-072e-4ed4-8130-2af1ccee6c1a" Name="Replication Job 3" />           <Link Rel="Alternate" Type="VAppReplicaPointReference" Href="https://localhost:9398/api/vAppReplicaPoints/7ba40ff8-2fd2-49e8-9c14-831f6e8203ca" Name="vApp002@2025-06-18 10:36:45" />           <Link Rel="Down" Type="VmReplicaPointReference" Href="https://localhost:9398/api/vmReplicaPoints/212893c9-d256-49da-88cc-c2328f121640" Name="AnT\_VM2-bRsW@2025-06-18 10:36:45" />         </Links>         <CreationTimeUTC>2025-06-18T10:36:45.317Z</CreationTimeUTC>         <VAppName>vApp002</VAppName>         <Algorithm>Full</Algorithm>         <PointType>Snapshot</PointType>       </VAppReplicaPoint>       <VAppReplicaPoint Type="VAppReplicaPoint" Href="https://localhost:9398/api/vAppReplicaPoints/af6a4fbd-47cf-4958-97f4-9942d595aa4d?format=Entity" Name="vApp002@2025-06-18 01:49:25" UID="urn:veeam:VAppReplicaPoint:af6a4fbd-47cf-4958-97f4-9942d595aa4d" VAppDisplayName="vApp002">         <Links>           <Link Rel="Failover" Href="https://localhost:9398/api/vAppReplicaPoints/af6a4fbd-47cf-4958-97f4-9942d595aa4d?action=failover" />           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Up" Type="ReplicaReference" Href="https://localhost:9398/api/replicas/057050bf-072e-4ed4-8130-2af1ccee6c1a" Name="Replication Job 3" />           <Link Rel="Alternate" Type="VAppReplicaPointReference" Href="https://localhost:9398/api/vAppReplicaPoints/af6a4fbd-47cf-4958-97f4-9942d595aa4d" Name="vApp002@2025-06-18 01:49:25" />           <Link Rel="Down" Type="VmReplicaPointReference" Href="https://localhost:9398/api/vmReplicaPoints/7fca8218-8c85-4c48-8ef7-95c0f524f683" Name="AnT\_VM1-Rtnu@2025-06-18 01:49:25" />         </Links>         <CreationTimeUTC>2025-06-18T01:49:25.397Z</CreationTimeUTC>         <VAppName>vApp002</VAppName>         <Algorithm>Full</Algorithm>         <PointType>Snapshot</PointType>       </VAppReplicaPoint>       <VAppReplicaPoint Type="VAppReplicaPoint" Href="https://localhost:9398/api/vAppReplicaPoints/af6a4fbd-47cf-4958-97f4-9942d595aa4d?format=Entity" Name="vApp002@2025-06-18 01:49:25" UID="urn:veeam:VAppReplicaPoint:af6a4fbd-47cf-4958-97f4-9942d595aa4d" VAppDisplayName="vApp002">         <Links>           <Link Rel="Failover" Href="https://localhost:9398/api/vAppReplicaPoints/af6a4fbd-47cf-4958-97f4-9942d595aa4d?action=failover" />           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Up" Type="ReplicaReference" Href="https://localhost:9398/api/replicas/057050bf-072e-4ed4-8130-2af1ccee6c1a" Name="Replication Job 3" />           <Link Rel="Alternate" Type="VAppReplicaPointReference" Href="https://localhost:9398/api/vAppReplicaPoints/af6a4fbd-47cf-4958-97f4-9942d595aa4d" Name="vApp002@2025-06-18 01:49:25" />           <Link Rel="Down" Type="VmReplicaPointReference" Href="https://localhost:9398/api/vmReplicaPoints/ed259562-5c9f-4235-890e-be2d3719010b" Name="AnT\_VM2-bRsW@2025-06-18 01:49:43" />         </Links>         <CreationTimeUTC>2025-06-18T01:49:25.397Z</CreationTimeUTC>         <VAppName>vApp002</VAppName>         <Algorithm>Full</Algorithm>         <PointType>Snapshot</PointType>       </VAppReplicaPoint>     </VAppReplicaPoints>   </Entities>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=VAppReplicaPoint&format=Entities&sortDesc=CreationTime&filter=VAppName==vApp002&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=VAppReplicaPoint&format=Entities&sortDesc=CreationTime&filter=VAppName==vApp002&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

