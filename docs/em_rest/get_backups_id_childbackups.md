---
title: "GET /backups/{ID}/childbackups"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_backups_id_childbackups.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /backups/{ID}/childbackups


Returns a resource representation of a collection of all [ChildBackup](get_backups_id.md#BackupType) resources of a [ParentBackup](get_backups_id.md#BackupType) backup type having the specified ID.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To get a list of child backups, send the GET HTTP request to the /backups/{ID}/childbackups resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/backups/{ID}/childbackups |

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

In the response body, the REST API returns a representation of the /backups/{ID}/childbackups resource collection.

Example

The example below returns a list of all child backups of a backup container having ID 7b6a400c-452c-41d1-bb81-ea682e89492d.

|  |
| --- |
| Request:  GET https://localhost:9398/api/backups/7b6a400c-452c-41d1-bb81-ea682e89492d/childbackups  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:Backup:da68ee31-a90b-44b7-bfab-a1eb49b9d352" Name="VM number 0 Backup (Simple backup)" Href="http://local.host:9399/api/backups/da68ee31-a90b-44b7-bfab-a1eb49b9d352" Type="BackupReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/repositories/b8832f03-2c9e-4222-8d0b-e43e0c912f93" Name="Scale-out Backup Repository 2" Type="RepositoryReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/da68ee31-a90b-44b7-bfab-a1eb49b9d352?format=Entity" Name="VM number 0 Backup (Simple backup)" Type="Backup" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backups/da68ee31-a90b-44b7-bfab-a1eb49b9d352/restorePoints" Type="RestorePointReferenceList" Rel="Down"/>       <Link Href="http://local.host:9399/api/backups/7b6a400c-452c-41d1-bb81-ea682e89492d" Name="Parent Backup" Type="BackupReference" Rel="Up"/>     </Links>   </Ref>   ... </EntityReferences> |

Page updated 2026-07-29

