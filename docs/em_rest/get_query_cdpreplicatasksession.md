---
title: "GET /query?type=CdpReplicaTaskSession"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_cdpreplicatasksession.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=CdpReplicaTaskSession


Returns a collection of CDP replication task sessions that run on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/cdpReplicaTaskSessions](cdpreplicatasksessions.md).

Request

To get a collection of CDP replication task sessions, send the GET HTTP request to the query with the type parameter set to CdpReplicaTaskSession.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=CdpReplicaTaskSession |

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
| Id | UidType | UID of the CDP replication task session, for example: urn:veeam:CdpReplicaTaskSession:ad86fed0-4288-47ba-a7ab-0fca64d3ba5a. |
| Name | String | Name of the CDP replication task session, for example: virt03-ubuntu01@2025-02-12 00:00:10. |
| PolicySessionUid | UidType | UID of the CDP policy session parent to the CDP replication task session resource, for example: urn:veeam:CdpReplicaSession:6b872a71-51e8-437a-8d45-5c6494b92f3f. |
| PolicySessionName | String | Name of the CDP policy session parent to the CDP replication task session resource. |
| BackupServerUid | UidType | UID of the backup server on which the CDP policy is created. |
| BackupServerName | String | Name of the backup server on which the CDP policy is created. |
| CreationTimeUTC | DateTime | Date and time when the CDP replication task session was started. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:30.389954Z. |
| EndTimeUTC | DateTime | Date and time when the CDP replication task session was ended. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:31.000000Z. |
| State | String | State of the CDP replication task session. Possible values:   * InProgress * Pending * Completed |
| Reason | String | Reason for which the CDP replication task session has been completed with the Warning or Failed result. |
| TotalSize | Long | Size of all restore points produced by the CDP replication task session. |
| VmDisplayName | String | Name of the VM that is processed in the CDP replication task session. |

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

In the response body, the REST API returns a representation of the /cdpReplicaTaskSessions resource collection.

Example

The example below returns an entity resource representation of a collection of CDP replication task sessions that were created for the virt03-ubuntu01 VM on June 15, 2025.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=CdpReplicaTaskSession&format=Entities&filter=CreationTimeUTC>="2025-06-15";CreationTimeUTC<="2025-06-16";VmDisplayName=="virt03-ubuntu01"  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <CdpReplicaTaskSessions>       <CdpReplicaTaskSession Type="CdpReplicaTaskSession" Href="https://localhost:9398/api/replicaTaskSessions/787d754e-6399-46f1-8199-2207f0e8fe20?format=Entity" Name="virt03-ubuntu01@2025-06-15 07:00:06" VmDisplayName="virt03-ubuntu01" UID="urn:veeam:CdpReplicaTaskSession:787d754e-6399-46f1-8199-2207f0e8fe20">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/beda8585-1354-451c-afe2-646dcf42afa6" Name="backupsrv29.tech.local" />           <Link Rel="Up" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/042da2cf-86a9-4d09-9766-be90f3ccd506" Name="CDP Policy@2025-06-14 15:00:24" />           <Link Rel="Alternate" Type="CdpReplicaTaskSessionReference" Href="https://localhost:9398/api/cdpReplicaTaskSessions/787d754e-6399-46f1-8199-2207f0e8fe20" Name="virt03-ubuntu01@2025-06-15 07:00:06" />         </Links>         <PolicySessionUid>urn:veeam:CdpReplicaSession:042da2cf-86a9-4d09-9766-be90f3ccd506</PolicySessionUid>         <CreationTimeUTC>2025-06-15T07:00:06.787Z</CreationTimeUTC>         <EndTimeUTC>2025-06-15T15:00:08.847Z</EndTimeUTC>         <State>Completed</State>         <Result>Success</Result>         <TotalSize>17179869184</TotalSize>       </CdpReplicaTaskSession>       <CdpReplicaTaskSession Type="CdpReplicaTaskSession" Href="https://localhost:9398/api/replicaTaskSessions/0e9b9a27-15fd-4dee-98f9-5a98f0d89a3e?format=Entity" Name="virt03-ubuntu01@2025-06-15 15:00:09" VmDisplayName="virt03-ubuntu01" UID="urn:veeam:CdpReplicaTaskSession:0e9b9a27-15fd-4dee-98f9-5a98f0d89a3e">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/beda8585-1354-451c-afe2-646dcf42afa6" Name="backupsrv29.tech.local" />           <Link Rel="Up" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/30a2b685-f858-4f15-9ef6-d3b007a99d2d" Name="CDP Policy@2025-06-15 15:00:08" />           <Link Rel="Alternate" Type="CdpReplicaTaskSessionReference" Href="https://localhost:9398/api/cdpReplicaTaskSessions/0e9b9a27-15fd-4dee-98f9-5a98f0d89a3e" Name="virt03-ubuntu01@2025-06-15 15:00:09" />         </Links>         <PolicySessionUid>urn:veeam:CdpReplicaSession:30a2b685-f858-4f15-9ef6-d3b007a99d2d</PolicySessionUid>         <CreationTimeUTC>2025-06-15T15:00:09.05Z</CreationTimeUTC>         <EndTimeUTC>2025-06-15T23:00:06.493Z</EndTimeUTC>         <State>Completed</State>         <Result>Success</Result>         <TotalSize>17179869184</TotalSize>       </CdpReplicaTaskSession>       <CdpReplicaTaskSession Type="CdpReplicaTaskSession" Href="https://localhost:9398/api/replicaTaskSessions/136e9284-b6b3-44f2-ad04-af57a610c3cd?format=Entity" Name="virt03-ubuntu01@2025-06-15 23:00:06" VmDisplayName="virt03-ubuntu01" UID="urn:veeam:CdpReplicaTaskSession:136e9284-b6b3-44f2-ad04-af57a610c3cd">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/beda8585-1354-451c-afe2-646dcf42afa6" Name="backupsrv29.tech.local" />           <Link Rel="Up" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/30a2b685-f858-4f15-9ef6-d3b007a99d2d" Name="CDP Policy@2025-06-15 15:00:08" />           <Link Rel="Alternate" Type="CdpReplicaTaskSessionReference" Href="https://localhost:9398/api/cdpReplicaTaskSessions/136e9284-b6b3-44f2-ad04-af57a610c3cd" Name="virt03-ubuntu01@2025-06-15 23:00:06" />         </Links>         <PolicySessionUid>urn:veeam:CdpReplicaSession:30a2b685-f858-4f15-9ef6-d3b007a99d2d</PolicySessionUid>         <CreationTimeUTC>2025-06-15T23:00:06.51Z</CreationTimeUTC>         <EndTimeUTC>2025-06-16T07:00:06.663Z</EndTimeUTC>         <State>Completed</State>         <Result>Success</Result>         <TotalSize>17179869184</TotalSize>       </CdpReplicaTaskSession>     </CdpReplicaTaskSessions>   </Entities>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=CdpReplicaTaskSession&format=Entities&filter=CreationTimeUTC%3e="2025-06-15";CreationTimeUTC>="2025-06-16";VmDisplayName=="virt03-ubuntu01"&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=CdpReplicaTaskSession&format=Entities&filter=CreationTimeUTC%3e="2025-06-15";CreationTimeUTC>="2025-06-16";VmDisplayName=="virt03-ubuntu01"&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-28

