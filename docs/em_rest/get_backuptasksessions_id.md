---
title: "get_backuptasksessions_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_backuptasksessions_id.html"
last_updated: "9/12/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a task having the specified ID. The parent backup job for the task is created and run on the backup server connected to Veeam Backup Enterprise Manager.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V
* Veeam Agent computers running Microsoft Windows or Linux

Request

To get a task having the specified ID, send the GET HTTP request to the URL of the /backupTaskSessions/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/backupTaskSessions/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /backupTaskSessions/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the backup task session. |
| Name | String | Name of the backup task session, for example: dc-hv@2013-08-25 05:01:09. |
| JobSessionUid | UidType | UID of the backup job session parent to the backup task session resource. |
| CreationTime | DateTime | Date and time when the backup task session was started. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:30.389954Z. |
| EndTime | DateTime | Date and time when the backup task session was ended. The parameter accepts only UTC-formatted DateTime values, for example: 2025-08-14T12:31:31.000000Z. |
| State | String | State of the backup task session. Possible values:   * InProgress * Pending * Completed |
| Result | String | Result of the backup task session. Possible values:   * Success * Warning * Failed |
| Reason | String | Reason for which the backup task session has been completed with the Warning or Failed result. |
| TotalSize | Long | Size of all restore points produced by the backup job. |
| VmUid | UidType | UID of the VM that is processed in the backup task session. |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=BackupTaskSession](get_query_backuptasksession.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| BackupServerReference | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — backup server where the related backup job was created. |
| BackupJobSessionReference | Up | URL of the [/backupSessions/{ID}](backupsessions_id.md) resource parent to the backup task session. |
| BackupTaskSessionReference | Alternate | Alternate URL of the [/backupTaskSessions/{ID}](backuptasksessions_id.md) resource. |
| VmRestorePoint | Related | URL of the [/vmRestorePoints/{ID}](vmrestorepoints_id.md) resource — a VM restore point created during the backup task session. |

Example

The example request below returns a resource representation of a task having ID 88322206-a645-4aa3-9228-028ce51e7c0f.

|  |
| --- |
| Request:  GET https://localhost:9398/api/backupTaskSessions/88322206-a645-4aa3-9228-028ce51e7c0f?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <?xml version="1.0" encoding="utf-8"?> |

Page updated 9/12/2025

Page content applies to build 13.0.1.1071
