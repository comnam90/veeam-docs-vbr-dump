---
title: "get_query_restoresession"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_restoresession.html"
last_updated: "9/12/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a collection of restore sessions performed on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/restoreSessions](restoresessions.md).

Request

To get a list of restore sessions, send the GET HTTP request to the query with the type parameter set to RestoreSession.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=RestoreSession |

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
| UID | UidType | UID of the restore session resource, for example: urn:veeam:RestoreSession:19d68dbb-0f96-431c-9e61-9f5342c41e7c. |
| Name | String | Name of the restore session resource, for example: sql02@2013-08-26 11:28:33. |
| Type | String | Type of the restore session. Possible values:   * FileLevelRestore * RestoreVm |
| CreationTime | DateTime | Date and time when the restore session was started. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:30.389954Z. |
| EndTime | DateTime | Date and time when the restore session was ended. The parameter accepts only UTC-formatted DateTime values |
| State | String | State of the restore session. Possible values:   * Starting * Stopping * Working * Stopped |
| Result | String | Result of the restore session. Possible values:   * Success * Warning * Failed |
| BackupServerUid | UidType | UID of the backup server parent to the restore session resource. |
| BackupServerName | String | Name of the backup server parent to the restore session resource. |
| VmDisplayName | String | Name of the VM for which the restore session has been started. |

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

In the response body, the REST API returns a representation of the /restoreSessions resource collection.

Example

The example below returns an entity resource representation of a collection of restore sessions started for the virt03-ubuntu01 VM.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=RestoreSession&format=Entities&filter=VmDisplayName=="virt03-ubuntu01"    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 9/12/2025

Page content applies to build 13.0.1.1071
