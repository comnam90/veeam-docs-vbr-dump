---
title: "GET /query?type=CdpReplicaSession"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_cdpreplicasession.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=CdpReplicaSession


Returns a collection of CDP replication sessions performed on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/cdpReplicaSessions](cdpreplicasessions.md).

Request

To get a collection of all CDP replication sessions, send the GET HTTP request to the query with the type parameter set to CdpReplicaSession.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=CdpReplicaSession |

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
| Id | UidType | ID of the CDP replication session, for example: urn:veeam:CdpReplicaSession:6b872a71-51e8-437a-8d45-5c6494b92f3f. |
| Name | String | Name of the CDP replication session, for example: CDP Policy 1@2025-02-11 19:08:36. |
| PolicyUid | UidType | UID of the CDP policy parent to the session, for example: urn:veeam:CdpPolicy:145f3365-6ec0-44e9-9538-8c8c34ebdcce. |
| PolicyName | String | Name of the CDP policy parent to the session, for example: CDP Policy 1. |
| BackupServerUid | UidType | UID of the backup server parent to the CDP replication session. |
| BackupServerName | String | Name of the backup server parent to the CDP replication session. |
| CreationTimeUTC | DateTime | Date and time when the session was started. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:30.389954Z. |
| EndTimeUTC | DateTime | Date and time when the session was ended. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:31.000000Z. |
| State | String | State of the CDP replication session. Possible values:   * Starting * Stopping * Working * Pausing * Resuming * Stopped |
| Result | String | Result of the CDP replication session. Possible values:   * Success * Warning * Failed |
| FailureMessage | String | Reason for which the CDP replication session has been completed with the Failed result. |

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

In the response body, the REST API returns a representation of the /cdpReplicaSessions resource collection.

Example

The example below returns an entity resource representation of a collection of CDP replication sessions that were created on June 15, 2025 or later.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=CdpReplicaSession&format=Entities&filter=CreationTimeUTC>="2025-06-15"  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <CdpReplicaSessions>       <CdpPolicySession Type="CdpReplicaSession" Href="https://localhost:9398/api/cdpReplicaSessions/d05b25d0-c55c-41dd-b1e3-cd7e454a1937?format=Entity" Name="CDP Policy@2025-06-16 15:00:53" UID="urn:veeam:CdpReplicaSession:d05b25d0-c55c-41dd-b1e3-cd7e454a1937">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/beda8585-1354-451c-afe2-646dcf42afa6" Name="backupsrv29.tech.local" />           <Link Rel="Up" Type="CdpPolicyReference" Href="https://localhost:9398/api/cdpPolicies/872a3860-3805-43b8-bcf6-388384bfed33" Name="CDP Policy" />           <Link Rel="Alternate" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/d05b25d0-c55c-41dd-b1e3-cd7e454a1937" Name="CDP Policy@2025-06-16 15:00:53" />           <Link Rel="Down" Type="CdpReplicaTaskSessionReferenceList" Href="https://localhost:9398/api/cdpReplicaSessions/d05b25d0-c55c-41dd-b1e3-cd7e454a1937/cdpReplicaTaskSessions" />         </Links>         <PolicyUid>urn:veeam:CdpPolicy:872a3860-3805-43b8-bcf6-388384bfed33</PolicyUid>         <PolicyName>CDP Policy</PolicyName>         <PolicyType>CdpReplica</PolicyType>         <CreationTimeUTC>2025-06-16T15:00:53.78Z</CreationTimeUTC>         <State>Working</State>         <Result>None</Result>         <Progress>0</Progress>         <FailureMessage />         <IsRetry>false</IsRetry>       </CdpPolicySession>       <CdpPolicySession Type="CdpReplicaSession" Href="https://localhost:9398/api/cdpReplicaSessions/30a2b685-f858-4f15-9ef6-d3b007a99d2d?format=Entity" Name="CDP Policy@2025-06-15 15:00:08" UID="urn:veeam:CdpReplicaSession:30a2b685-f858-4f15-9ef6-d3b007a99d2d">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/beda8585-1354-451c-afe2-646dcf42afa6" Name="backupsrv29.tech.local" />           <Link Rel="Up" Type="CdpPolicyReference" Href="https://localhost:9398/api/cdpPolicies/872a3860-3805-43b8-bcf6-388384bfed33" Name="CDP Policy" />           <Link Rel="Alternate" Type="CdpReplicaSessionReference" Href="https://localhost:9398/api/cdpReplicaSessions/30a2b685-f858-4f15-9ef6-d3b007a99d2d" Name="CDP Policy@2025-06-15 15:00:08" />           <Link Rel="Down" Type="CdpReplicaTaskSessionReferenceList" Href="https://localhost:9398/api/cdpReplicaSessions/30a2b685-f858-4f15-9ef6-d3b007a99d2d/cdpReplicaTaskSessions" />         </Links>         <PolicyUid>urn:veeam:CdpPolicy:872a3860-3805-43b8-bcf6-388384bfed33</PolicyUid>         <PolicyName>CDP Policy</PolicyName>         <PolicyType>CdpReplica</PolicyType>         <CreationTimeUTC>2025-06-15T15:00:08.847Z</CreationTimeUTC>         <EndTimeUTC>2025-06-16T15:00:53.78Z</EndTimeUTC>         <State>Stopped</State>         <Result>Failed</Result>         <Progress>0</Progress>         <FailureMessage />         <IsRetry>false</IsRetry>       </CdpPolicySession>     </CdpReplicaSessions>   </Entities>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=CdpReplicaSession&format=Entities&filter=CreationTimeUTC%3e="2025-06-15"&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=CdpReplicaSession&format=Entities&filter=CreationTimeUTC%3e="2025-06-15"&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-28

