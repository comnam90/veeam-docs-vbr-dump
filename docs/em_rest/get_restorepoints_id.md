---
title: "GET /restorePoints/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_restorepoints_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
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

Request Headers

| Header | Required | Description |
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

Response Headers

| Header | Description |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns an entity or an entity reference of the /restorePoints/{ID} resource. The resource entity contains the following parameters and links.

Parameters

Response Body

| Element | Type | Description |
| UID | UidType | UID of the restore point resource, for example: urn:veeam:RestorePoint:bf0542a7-baea-41fa-baec-12e76043d0e1 |
| Name | String | Name of the restore point, for example: Aug 26 2025 7:57AM. |
| BackupDateUTC | DateTime | Date and time when the restore point was created. |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=RestorePoint](get_query_restorepoint.md).

Links

Response Body

| Reference | Relationship | Description |
| /backups/{ID} | Up | URL of the [/backups/{ID}](backups_id.md) resource — a backup that contains the restore point. |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server that created the restore point. |
| /restorePoints/{ID} | Alternate | Alternate URL of the [/restorePoints/{ID}](restorepoints_id.md) resource. |
| /restorePoints/{ID}/vmRestorePoints | Down | URL of the [/restorePoints/{ID}/vmRestorePoints](restorepoints_id_vmrestorepoints.md) resource — a collection of VM restore points created for the restore point. |
| /restorePoints/{ID}/backupFiles | Down | URL of the [/restorePoints/{ID}/backupFiles](restorepoints_id_backupfiles.md) resource — a collection of backup files created for the restore point. |

Example

A sample request below returns an entity resource representation of a restore point having ID 4efa47e0-c3bd-47f2-a87a-013088f8b495.

|  |
| --- |
| Request:  GET https://localhost:9398/api/restorePoints/4efa47e0-c3bd-47f2-a87a-013088f8b495?format=Entity  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <?xml version="1.0" encoding="utf-8"?> <RestorePoint xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" Href="https://enterprise04.tech.local:9398/api/restorePoints/4efa47e0-c3bd-47f2-a87a-013088f8b495?format=Entity" Type="RestorePoint" Name="Oct 14 2025  8:00PM" UID="urn:veeam:RestorePoint:4efa47e0-c3bd-47f2-a87a-013088f8b495" xmlns="http://www.veeam.com/ent/v1.0">     <Links>         <Link Href="https://enterprise04.tech.local:9398/api/backups/2e734096-56ea-4f36-ac2a-15546518d26c" Name="Backup Job 3" Type="BackupReference" Rel="Up" />         <Link Href="https://enterprise04.tech.local:9398/api/backupServers/a490c017-2c1c-40ee-8bcf-73bcce6ab36f" Name="enterprise01.tech.local" Type="BackupServerReference" Rel="Up" />         <Link Href="https://enterprise04.tech.local:9398/api/restorePoints/4efa47e0-c3bd-47f2-a87a-013088f8b495" Name="Oct 14 2025  8:00PM" Type="RestorePointReference" Rel="Alternate" />         <Link Href="https://enterprise04.tech.local:9398/api/restorePoints/4efa47e0-c3bd-47f2-a87a-013088f8b495/vmRestorePoints" Type="VmRestorePointReferenceList" Rel="Down" />         <Link Href="https://enterprise04.tech.local:9398/api/restorePoints/4efa47e0-c3bd-47f2-a87a-013088f8b495/backupFiles" Type="BackupFileReferenceList" Rel="Related" />     </Links>     <BackupDateUTC>2025-10-14T20:00:31.23Z</BackupDateUTC> </RestorePoint> |

Page updated 2026-07-29

