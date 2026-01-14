---
title: "get_cdpreplicatasksessions_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cdpreplicatasksessions_id.html"
last_updated: "9/12/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a CDP replication task session having the specified ID.

Request

To get a CDP replication task session having the specified ID, send the GET HTTP request to the /cdpReplicaTaskSessions/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cdpReplicaTaskSessions/{ID} |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

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

In the response body, the REST API returns an entity or an entity reference of the /cdpReplicaTaskSessions/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the CDP replication task session, for example: urn:veeam:CdpReplicaTaskSession:ad86fed0-4288-47ba-a7ab-0fca64d3ba5a. |
| Name | String | Name of the CDP replication task session, for example: virt03-ubuntu01@2021-02-12 00:00:10. |
| PolicySessionUid | UidType | UID of the CDP policy session parent to the CDP replication task session resource, for example: urn:veeam:CdpReplicaSession:6b872a71-51e8-437a-8d45-5c6494b92f3f. |
| CreationTimeUTC | DateTime | Date and time when the CDP replication task session was launched. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:30.389954Z. |
| EndTimeUTC | DateTime | Date and time when the CDP replication task session was completed. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:31.000000Z. |
| State | String | State of the CDP replication task session. Possible values:   * InProgress * Pending * Completed |
| Result | String | Result of the CDP replication task session. Possible values:   * Success * Warning * Failed |
| Reason | String | Reason for which the CDP replication task session has been completed with the Warning or Failed result. |
| TotalSize | Long | Size of all restore points produced by the CDP replication task session. |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=CdpReplicaTaskSession](get_query_cdpreplicatasksession.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the CDP policy was configured. |
| /cdpReplicaSessions/{ID} | Up | URL of the [/cdpReplicaSessions/{ID}](cdpreplicasessions_id.md) resource — a parent CDP replication session. |
| /cdpReplicaTaskSessions/{ID} | Alternate | Alternate URL of the [/cdpReplicaTaskSessions/{ID}](cdpreplicatasksessions_id.md) resource. |

Example

The example request below returns an entity resource representation of a CDP replication task session having ID 2ec4d35f-b5d8-4cb3-9d11-12e1d5792625:

|  |
| --- |
| Request:  GET https://localhost:9398/api/cdpReplicaTaskSessions/2ec4d35f-b5d8-4cb3-9d11-12e1d5792625?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body: |

Page updated 9/12/2025

Page content applies to build 13.0.1.1071
