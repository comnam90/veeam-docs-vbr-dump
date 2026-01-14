---
title: "get_query_replicatasksession"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_replicatasksession.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a collection of replication task sessions performed on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/replicaTaskSessions](replicatasksessions.md).

Request

To get a list of replication task sessions, send the GET HTTP request to the query with the type parameter set to ReplicaTaskSession.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=ReplicaTaskSession |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Optional Parameters

In the query, you can use the following parameters for filtering and sorting.

| Parameter | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the replication task session. |
| Name | String | Name of the replication task session, for example: dc-hv@2013-08-25 05:01:09. |
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

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns a representation of the /replicaTaskSessions resource collection.

Example

The example below returns an entity resource representation of a collection of replication task sessions started for VM apache02 and that were completed successfully. The results are ordered in the descending order by the CreationTime parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=ReplicaTaskSession&format=Entities&sortDesc=CreationTime&filter=Result==Success;VmDisplayName==apache02    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
