---
title: "GET /replicaTaskSessions/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_replicatasksessions_id.html"
last_updated: "9/12/2025"
product_version: "13.0.1.1071"
---

# GET /replicaTaskSessions/{ID}


Returns a resource representation of a replication task session having the specified ID.

Request

To get a replication task session having the specified ID, send the GET HTTP request to the /replicaTaskSessions/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/replicaTaskSessions/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /replicaTaskSessions/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the replication task session. |
| Name | String | Name of the replication task session, for example: dc-hv@2013-08-25 05:01:09. |
| JobSessionUid | UidType | UID of the replication job session parent to the replication task session resource. |
| CreationTime | DateTime | Date and time when the replication task session was started. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:30.389954Z. |
| EndTime | DateTime | Date and time when the replication task session was ended. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:31.000000Z. |
| State | String | State of the replication task session. Possible values:   * InProgress * Pending * Completed |
| Result | String | Result of the replication task session. Possible values:   * Success * Warning * Failed |
| Reason | String | Reason for which the replication task session has been completed with the Warning or Failed result. |
| TotalSize | Long | Size of all restore points produced by the replication job. |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=ReplicaTaskSession](get_query_replicatasksession.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the parent replication job was configured. |
| /replicaSessions/{ID} | Up | URL of the [/replicaSessions/{ID}](replicasessions_id.md) resource — a parent replication job session. |
| /replicaTaskSessions/{ID} | Alternate | Alternate URL of the [/replicaTaskSessions/{ID}](replicatasksessions_id.md) resource. |

Example

The example request below returns an entity resource representation of a task session having ID 809564f0-d2e7-4ee2-af2f-06d385138be2:

|  |
| --- |
| Request:  GET https://localhost:9398/api/replicaTaskSessions/809564f0-d2e7-4ee2-af2f-06d385138be2?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <?xml version="1.0" encoding="utf-8"?> |


