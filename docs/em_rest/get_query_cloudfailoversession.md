---
title: "GET /query?type=CloudFailoverSession"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_cloudfailoversession.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=CloudFailoverSession


Returns a collection of cloud failover sessions performed on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/cloud/failoverSessions](cloudfailoversessions.md).

Request

To get a list of cloud failover sessions, send the GET HTTP request to the query with the type parameter set to CloudFailoverSession.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=CloudFailoverSession |

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
| UID | UidType | UID of the cloud failover session resource, for example: 475420ee-d045-4493-9869-0a970e08f6f9. |
| Name | String | Name of the cloud failover session resource, for example: ABC Company Failover Plan. |
| Type | String | Type of the cloud failover session. Possible value: FailoverPlan. |
| CreationTime | DateTime | Date and time when the cloud failover session was started. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:30.389954Z. |
| EndTime | DateTime | Date and time when the cloud failover session was ended. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:31.000000Z. |
| State | String | State of the cloud failover session. Possible values:   * Starting * Stopping * Working * Stopped |
| Result | String | Result of the cloud failover session. Possible values:   * Success * Warning * Failed |
| FailureMessage | String | Reason for which the cloud replication session has been completed with the Failed result. |
| BackupServerUid | UidType | UID of the backup server parent to the cloud failover session resource. |
| BackupServerName | String | Name of the backup server parent to the cloud failover session resource. |

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

In the response body, the REST API returns a representation of the /cloud/failoverSessions resource collection.

Example

The example below returns an entity resource representation of a collection of failed cloud failover sessions. The results are ordered in the descending order by the CreationTime parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=CloudFailoverSession&format=Entities&sortDesc=CreationTime&filter=Result==failed  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <CloudFailoverSessions>       <CloudFailoverSession Type="CloudFailoverSession" Href="https://localhost:9398/api/cloud/failoverSessions/12295005-66e6-477d-a6d3-1401dd27476e?format=Entity" Name="ABC Company Failover Plan" UID="urn:veeam:CloudFailoverSession:12295005-66e6-477d-a6d3-1401dd27476e">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ca19249e-e638-421a-ab22-68cb89b9009a" Name="172.24.31.67" />           <Link Rel="Alternate" Type="CloudFailoverSessionReference" Href="https://localhost:9398/api/cloud/failoverSessions/12295005-66e6-477d-a6d3-1401dd27476e" Name="ABC Company Failover Plan" />         </Links>         <JobType>FailoverPlan</JobType>         <CreationTimeUTC>2025-01-13T16:21:35.74Z</CreationTimeUTC>         <EndTimeUTC>2025-01-13T16:23:16.11Z</EndTimeUTC>         <State>Stopped</State>         <Result>Failed</Result>         <Progress>100</Progress>         <CloudFailoverTasks />       </CloudFailoverSession>     </CloudFailoverSessions>   </Entities>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=CloudFailoverSession&format=Entities&sortDesc=CreationTime&filter=Result==failed&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=CloudFailoverSession&format=Entities&sortDesc=CreationTime&filter=Result==failed&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-28

