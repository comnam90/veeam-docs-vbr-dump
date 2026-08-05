---
title: "GET /backups/{ID}/restorePoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_backups_id_restorepoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /backups/{ID}/restorePoints


Returns a resource representation of a collection of restore points of [Standard and ChildBackup](get_backups_id.md#BackupType) backups having the specified ID.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To get a list of restore points, send the GET HTTP request to the /backups/{ID}/restorePoints resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/backups/{ID}/restorePoints |

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

In the response body, the REST API returns a representation of the /backups/{ID}/restorePoints resource collection.

Example

The example below returns a list of all restore points of a backup having ID 7b6a400c-452c-41d1-bb81-ea682e89492d.

|  |
| --- |
| Request:  GET https://localhost:9398/api/backups/7b6a400c-452c-41d1-bb81-ea682e89492d/restorePoints  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <?xml version="1.0" encoding="utf-8"?> <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:RestorePoint:ec940768-5428-41af-b9b6-afad2aefe9d6" Name="Jan 17 2025  5:21PM" Href="https://localhost:9398/api/restorePoints/ec940768-5428-41af-b9b6-afad2aefe9d6" Type="RestorePointReference">     <Links>       <Link Href="https://localhost:9398/api/backupServers/4ad6fa62-9164-4ea0-87c8-1e2d071d60de" Name="srv30" Type="BackupServerReference" Rel="Up"/>       <Link Href="https://localhost:9398/api/backups/7b6a400c-452c-41d1-bb81-ea682e89492d" Name="WindowsFileLevelRestoreFromCatalog" Type="BackupReference" Rel="Up"/>       <Link Href="https://localhost:9398/api/restorePoints/ec940768-5428-41af-b9b6-afad2aefe9d6?format=Entity" Name="Jan 17 2025  5:21PM" Type="RestorePoint" Rel="Alternate"/>       <Link Href="https://localhost:9398/api/restorePoints/ec940768-5428-41af-b9b6-afad2aefe9d6/vmRestorePoints" Type="VmRestorePointReferenceList" Rel="Down"/>       <Link Href="https://localhost:9398/api/restorePoints/ec940768-5428-41af-b9b6-afad2aefe9d6/backupFiles" Type="RestorePointReferenceList" Rel="Related"/>     </Links>   </Ref>   ... </EntityReferences> |

Page updated 2026-07-29

