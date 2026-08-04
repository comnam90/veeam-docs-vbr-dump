---
title: "GET /query?type=ReplicaTaskSession"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_replicatasksession.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=ReplicaTaskSession


Returns a resource representation of a collection of replication task sessions performed on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/replicaTaskSessions](replicatasksessions.md).

Request

To get a list of replication task sessions, send the GET HTTP request to the query with the type parameter set to ReplicaTaskSession.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=ReplicaTaskSession |

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
| UID | UidType | UID of the replication task session. |
| Name | String | Name of the replication task session, for example: dc-hv@2025-08-25 05:01:09. |
| CreationTime | DateTime | Date and time when the replication task session was launched. The parameter accepts only UTC-formatted DateTime values. |
| EndTime | DateTime | Date and time when the replication task session was completed. The parameter accepts only UTC-formatted DateTime values. |
| State | String | State of the replication task session. Possible values:   * InProgress * Pending * Completed |
| Result | String | Result of the replication task session. Possible values:   * Success * Warning * Failed |
| Reason | String | Reason for which the replication task session has been completed with the Warning or Failed result. |
| TotalSize | Long | Size of all restore points produced by the replication job. |
| JobSessionUid | UidType | UID of the replication job session parent to the replication task session resource. |
| JobUid | UidType | UID of the replication job parent to the replication task session resource. |
| JobName | String | Name of the replication job parent to the replication task session resource. |
| BackupServerUid | UidType | UID of the backup server on which the replication job is created. |
| BackupServerName | String | Name of the backup server on which the replication job is created. |
| VmDisplayName | String | Name of the VM that is processed in the replication task session. |

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

In the response body, the REST API returns a representation of the /replicaTaskSessions resource collection.

Example

The example below returns an entity resource representation of a collection of replication task sessions started for VM apache02 and that were completed successfully. The results are ordered in the descending order by the CreationTime parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=ReplicaTaskSession&format=Entities&sortDesc=CreationTime&filter=Result==Success;VmDisplayName==apache02  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <ReplicaTaskSessions>       <ReplicaTaskSession Type="ReplicaTaskSession" Href="https://localhost:9398/api/replicaTaskSessions/efe448ad-6d52-496b-ba79-decd586713eb?format=Entity" Name="apache02@2025-06-17 20:00:18" VmDisplayName="apache02" UID="urn:veeam:ReplicaTaskSession:efe448ad-6d52-496b-ba79-decd586713eb">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Up" Type="ReplicaJobSessionReference" Href="https://localhost:9398/api/replicaSessions/90e440bb-8af1-4e3f-8022-bfd89dd267a0" Name="Replication Job 2@2025-06-17 20:00:05" />           <Link Rel="Alternate" Type="ReplicaTaskSessionReference" Href="https://localhost:9398/api/replicaTaskSessions/efe448ad-6d52-496b-ba79-decd586713eb" Name="apache02@2025-06-17 20:00:18" />         </Links>         <JobSessionUid>urn:veeam:ReplicaJobSession:90e440bb-8af1-4e3f-8022-bfd89dd267a0</JobSessionUid>         <CreationTimeUTC>2025-06-17T20:00:18.06Z</CreationTimeUTC>         <EndTimeUTC>2025-06-17T20:02:36.993Z</EndTimeUTC>         <State>Completed</State>         <Result>Success</Result>         <Reason />         <TotalSize>8589934592</TotalSize>       </ReplicaTaskSession>       <ReplicaTaskSession Type="ReplicaTaskSession" Href="https://localhost:9398/api/replicaTaskSessions/3be8eb42-7d94-4789-b2cf-891a2d9aed41?format=Entity" Name="apache02@2025-06-17 15:17:00" VmDisplayName="apache02" UID="urn:veeam:ReplicaTaskSession:3be8eb42-7d94-4789-b2cf-891a2d9aed41">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Up" Type="ReplicaJobSessionReference" Href="https://localhost:9398/api/replicaSessions/c73c05f9-1f01-4a72-8126-c8fc8ed2df12" Name="Replication Job 2@2025-06-17 15:16:53" />           <Link Rel="Alternate" Type="ReplicaTaskSessionReference" Href="https://localhost:9398/api/replicaTaskSessions/3be8eb42-7d94-4789-b2cf-891a2d9aed41" Name="apache02@2025-06-17 15:17:00" />         </Links>         <JobSessionUid>urn:veeam:ReplicaJobSession:c73c05f9-1f01-4a72-8126-c8fc8ed2df12</JobSessionUid>         <CreationTimeUTC>2025-06-17T15:17:00.38Z</CreationTimeUTC>         <EndTimeUTC>2025-06-17T15:19:31.547Z</EndTimeUTC>         <State>Completed</State>         <Result>Success</Result>         <Reason />         <TotalSize>8589934592</TotalSize>       </ReplicaTaskSession>     </ReplicaTaskSessions>   </Entities>   <PagingInfo PagesCount="1" PageSize="15" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=ReplicaTaskSession&format=Entities&sortDesc=CreationTime&pageSize=15&page=1&filter=Result==Success;VmDisplayName==apache02" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=ReplicaTaskSession&format=Entities&sortDesc=CreationTime&pageSize=15&page=1&filter=Result==Success;VmDisplayName==apache02" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

