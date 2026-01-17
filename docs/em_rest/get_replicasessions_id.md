---
title: "GET /replicaSessions/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_replicasessions_id.html"
last_updated: "9/12/2025"
product_version: "13.0.1.1071"
---

# GET /replicaSessions/{ID}


Returns a resource representation of a replication job session having the specified ID.

Request

To get a job session, send the GET HTTP request to the /replicaSessions/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/replicaSessions/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /replicaSessions/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the replication job session resource, for example: urn:veeam:ReplicaJobSession:88b395e2-81ff-439c-558c-188d97274c15. |
| Name | String | Name of the replication job session resource, for example: exch@2013-08-26 22:28:51. |
| JobUid | UidType | UID of the replication job parent to the replication job session resource, for example: urn:veeam:Job:dce85686-59c8-42c4-8766-f1c00a5b8067. |
| JobName | String | Name of the replication job parent to the replication job session resource, for example: SQL Replica. |
| JobType | String | Type of the replication job session. Possible values: Replica. |
| CreationTime | DateTime | Date and time when the replication job session was started. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:30.389954Z. |
| EndTime | DateTime | Date and time when the replication job session was ended. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:31.000000Z. |
| State | String | State of the replication job session. Possible values:   * Starting * Stopping * Working * Pausing * Resuming * Stopped |
| Result | String | Result of the replication job session. Possible values:   * Success * Warning * Failed |
| Progress | Int | Progress of the replication job session (between 1 and 100). |
| IsRetry | Boolean | Defines whether the replication job session has been retried or not. Possible values:   * True * False |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=ReplicaJobSession](get_query_replicajobsession.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the replication job was configured. |
| /jobs/{ID} | Up | URL of the [/jobs/{ID}](jobs_id.md) resource — a job that processes the replica. |
| /replicaSessions/{ID} | Alternate | Alternate URL of the [/replicaSessions/{ID}](replicasessions_id.md) resource. |
| /replicaSessions/{ID}/replicaTaskSessions | Down | URL of the [/replicaTaskSessions](replicatasksessions.md) resource — a collection of replication task sessions of the replication session. |

Example

A sample request below returns an entity representation of the replication job session resource having ID 04f694ad-664c-4603-a747-00edecae4f17.

|  |
| --- |
| Request:  GET https://localhost:9398/api/replicaSessions/04f694ad-664c-4603-a747-00edecae4f17?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <?xml version="1.0" encoding="utf-8"?> |


