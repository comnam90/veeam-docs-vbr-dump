---
title: "GET /restorePoints/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_restorepoints_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# GET /restorePoints/{ID}


Returns a resource representation of a backup restore point having the specified ID.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To get a restore point, send the GET HTTP request to the /restorePoints/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/restorePoints/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /restorePoints/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the restore point resource, for example: urn:veeam:RestorePoint:bf0542a7-baea-41fa-baec-12e76043d0e1 |
| Name | String | Name of the restore point, for example: Aug 26 2013 7:57AM. |
| BackupDateUTC | DateTime | Date and time when the restore point was created. |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=RestorePoint](get_query_restorepoint.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backups/{ID} | Up | URL of the [/backups/{ID}](backups_id.md) resource — a backup that contains the restore point. |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server that created the restore point. |
| /restorePoints/{ID} | Alternate | Alternate URL of the [/restorePoints/{ID}](restorepoints_id.md) resource. |
| /restorePoints/{ID}/vmRestorePoints | Down | URL of the [/restorePoints/{ID}/vmRestorePoints](restorepoints_id_vmrestorepoints.md) resource — a collection of VM restore points created for the restore point. |
| /restorePoints/{ID}/backupFiles | Down | URL of the [/restorePoints/{ID}/backupFiles](restorepoints_id_backupfiles.md) resource — a collection of backup files created for the restore point. |

Example

A sample request below returns an entity resource representation of a restore point having ID 4efa47e0-c3bd-47f2-a87a-013088f8b495.

|  |
| --- |
| Request:  GET https://localhost:9398/api/restorePoints/4efa47e0-c3bd-47f2-a87a-013088f8b495?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <?xml version="1.0" encoding="utf-8"?> |


