---
title: "GET /query?type=CdpReplicaTaskSession"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_cdpreplicatasksession.html"
last_updated: "9/12/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a collection of CDP replication task sessions that run on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/cdpReplicaTaskSessions](cdpreplicatasksessions.md).

Request

To get a collection of CDP replication task sessions, send the GET HTTP request to the query with the type parameter set to CdpReplicaTaskSession.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=CdpReplicaTaskSession |

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
| Id | UidType | UID of the CDP replication task session, for example: urn:veeam:CdpReplicaTaskSession:ad86fed0-4288-47ba-a7ab-0fca64d3ba5a. |
| Name | String | Name of the CDP replication task session, for example: virt03-ubuntu01@2021-02-12 00:00:10. |
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

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns a representation of the /cdpReplicaTaskSessions resource collection.

Example

The example below returns an entity resource representation of a collection of CDP replication task sessions that were created for the virt03-ubuntu01 VM on June 15, 2021.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=CdpReplicaTaskSession&format=Entities&filter=CreationTimeUTC>="2021-06-15";CreationTimeUTC<="2021-06-16";VmDisplayName=="virt03-ubuntu01"    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 9/12/2025

Page content applies to build 13.0.1.1071
