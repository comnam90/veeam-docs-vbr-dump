---
title: "GET /query?type=ReplicaJobSession"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_replicajobsession.html"
last_updated: "9/12/2025"
product_version: "13.0.1.1071"
---

# GET /query?type=ReplicaJobSession


Returns a resource representation of a collection of replication job sessions performed on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/replicaSessions](replicasessions.md).

Request

To get a list of replication job sessions, send the GET HTTP request to the query with the type parameter set to ReplicaJobSession.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=ReplicaJobSession |

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
| UID | UidType | UID of the replication job session resource, for example: urn:veeam:ReplicaJobSession:751b865f-6618-469e-80a4-003c55d09019. |
| Name | String | Name of the replication job session resource, for example: exch@2013-08-26 22:28:51. |
| JobType | String | Type of the replication job session. Possible values: Replica. |
| JobUid | UidType | ID of the replication job parent to the replication job session resource, for example: urn:veeam:Job:dce85686-59c8-42c4-8766-f1c00a5b8067. |
| JobName | String | Name of the replication job parent to the replication job session resource, for example: SQL Replica. |
| CreationTime | DateTime | Date and time when the replication job session was started. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:30.389954Z. |
| EndTime | DateTime | Date and time when the replication job session was ended. The parameter accepts only UTC-formatted DateTime values |
| State | String | State of the replication job session. Possible values:   * Starting * Stopping * Working * Pausing * Resuming * Stopped |
| Result | String | Result of the replication job session. Possible values:   * Success * Warning * Failed |
| IsRetry | Boolean | Defines whether the replication job session has been retried or not. Possible values:   * True * False |
| BackupServerUid | UidType | UID of the backup server parent to the replication job session resource. |
| BackupServerName | String | Name of the backup server parent to the replication session resource. |

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

In the response body, the REST API returns a representation of the /replicaSessions resource collection.

Example

The example below returns an entity resource representation of a collection of successful replication sessions started by the enterprise06.tech.local backup server.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=ReplicaJobSession&format=Entities&filter=BackupServerName=="enterprise06.tech.local";Result==Success    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |


