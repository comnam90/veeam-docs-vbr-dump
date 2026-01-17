---
title: "GET /query?type=CloudFailoverSession"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_cloudfailoversession.html"
last_updated: "9/12/2025"
product_version: "13.0.1.1071"
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

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns a representation of the /cloud/failoverSessions resource collection.

Example

The example below returns an entity resource representation of a collection of failed cloud failover sessions. The results are ordered in the descending order by the CreationTime parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=CloudFailoverSession&format=Entities&sortDesc=CreationTime&filter=Result==failed    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |


