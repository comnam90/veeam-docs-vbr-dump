---
title: "get_query_backupjobsession"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_backupjobsession.html"
last_updated: "9/12/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a collection of backup job sessions performed on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/backupSessions](backupsessions.md).

Request

To get a list of backup job sessions, send the GET HTTP request to the query with the type parameter set to BackupJobSession.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=BackupJobSession |

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
| UID | UidType | UID of the backup job session resource, for example: 88b395e2-81ff-439c-558c-188d97274c15. |
| Name | String | Name of the backup job session resource, for example: exch@2013-08-26 22:28:51. |
| JobType | String | Type of the backup job session. Possible values:   * Backup — VM backup job session. * BackupCopy — periodic backup copy job session. * ImmediateBackupCopy — immediate backup copy job session. * ImmediateBackupCopyWorker — child immediate backup copy job session that processes restore points of a specific source backup job. * AgentBackup — Veeam Agent backup job session. Represents a Veeam Agent backup job session container state and progress, contains links for child Veeam Agent backup job sessions. * AgentManagement — Veeam Agent child job session. Represents a Veeam Agent protected machine backup state and backup progress, contains links for restore points and the parent backup job session. * NasBackup — file share backup job session. |
| JobUid | UidType | UID of the backup job parent to the backup job session resource, for example: urn:veeam:Job:dce85686-59c8-42c4-8766-f1c00a5b8067. |
| JobName | String | Name of the backup job parent to the backup job session resource, for example: SQL Backup. |
| CreationTime | DateTime | Date and time when the backup job session was started. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:30.389954Z. |
| EndTime | DateTime | Date and time when the backup job session was ended. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:31.000000Z. |
| State | String | State of the backup job session. Possible values:   * Starting * Stopping * Working * Pausing * Resuming * Stopped |
| Result | String | Result of the backup job session. Possible values:   * Success * Warning * Failed |
| IsRetry | Boolean | Defines whether the backup job session has been retried or not. Possible values:   * True * False |
| BackupServerUid | UidType | UID of the backup server parent to the backup job session resource. |
| BackupServerName | String | Name of the backup server parent to the backup session resource. |

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

In the response body, the REST API returns a representation of the /backupSessions resource collection.

Example

The following example returns an entity resource representation of a collection of failed backup job sessions. The sessions must have started no earlier than August 15, 2025, at 6:00 AM GMT (2025-08-15T06:00:00Z) and no later than August 16, 2025, at 1:00 PM GMT (2025-08-16T13:00:00Z).

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=BackupJobSession&format=Entities&filter=Result==Failed;CreationTime>="2025-08-15T06:00:00Z";CreationTime<="2025-08-16T13:00:00Z"    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 9/12/2025

Page content applies to build 13.0.1.1071
