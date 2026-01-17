---
title: "GET /query?type=BackupTaskSession"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_backuptasksession.html"
last_updated: "9/12/2025"
product_version: "13.0.1.1071"
---

# GET /query?type=BackupTaskSession


Returns a resource representation of a collection of backup task sessions that are performed on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/backupTaskSessions](backuptasksessions.md).

Request

To get a list of backup task sessions, send the GET HTTP request to the query with the type parameter set to BackupTaskSession.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=BackupTaskSession |

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
| UID | UidType | ID of the backup task session. |
| Name | String | Name of the backup task session, for example: dc-hv@2013-08-25 05:01:09. |
| CreationTime | DateTime | Date and time when the backup task session was started. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:30.389954Z. |
| EndTime | DateTime | Date and time when the backup task session was ended. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:31.000000Z. |
| State | String | State of the backup task session. Possible values:   * InProgress * Pending * Completed |
| Result | String | Result of the backup task session. Possible values:   * Success * Warning * Failed |
| Reason | String | Reason for which the backup task session has been completed with the Warning or Failed result. |
| TotalSize | Long | Size of all restore points produced by the backup job. |
| JobSessionUid | UidType | UID of the backup job session parent to the backup task session resource. |
| JobUid | UidType | UID of the backup job parent to the backup task session resource. |
| JobName | String | Name of the backup job parent to the backup task session resource. |
| BackupServerUid | UidType | UID of the backup server on which the backup job is created. |
| BackupServerName | String | Name of the backup server on which the backup job is created. |
| VmDisplayName | String | Name of the VM that is processed in the backup task session. |

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

In the response body, the REST API returns a representation of the /backupTaskSessions resource collection.

Example

The example below returns an entity resource representation of a collection of last 3 backup task sessions started for VM dbserver01 and that were failed. The results are ordered in the descending order by the CreationTime parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=BackupTaskSession&format=Entities&sortDesc=CreationTime&pageSize=3&page=1&filter=Result==Failed;VmDisplayName==dbserver01    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |


