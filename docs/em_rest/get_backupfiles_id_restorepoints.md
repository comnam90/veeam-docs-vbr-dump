---
title: "GET /backupFiles/{ID}/restorePoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_backupfiles_id_restorepoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /backupFiles/{ID}/restorePoints


Returns a collection of restore points for a backup file with the specified ID. The backup file was created on or imported to the backup server connected to Veeam Backup Enterprise Manager.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To get a collection of restore points for a backup file, send the GET HTTP request to the /backupFiles/{ID}/restorePoints resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/backupFiles/{ID}/restorePoints |

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

In the response body, the REST API returns a representation of the /backupFiles/{ID}/restorePoints resource.

Example

The example below returns a collection of restore points for a backup file with ID 6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4.

|  |
| --- |
| Request:  GET https://localhost:9398/api/backupFiles/6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4/restorePoints  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/33732b87-1074-4883-bc3c-25931fbea4ed" Name="Sep 19 2025  9:00PM" UID="urn:veeam:RestorePoint:33732b87-1074-4883-bc3c-25931fbea4ed">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/99f01406-ecdc-428f-ae09-a13de244140a" Name="172.17.53.1" />       <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/80672bda-76a8-408b-947f-afd0ff67fba6" Name="Webserver Backup Copy" />       <Link Rel="Alternate" Type="RestorePoint" Href="https://localhost:9398/api/restorePoints/33732b87-1074-4883-bc3c-25931fbea4ed?format=Entity" Name="Sep 19 2025  9:00PM" />       <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/33732b87-1074-4883-bc3c-25931fbea4ed/vmRestorePoints" />       <Link Rel="Down" Type="VAppRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/33732b87-1074-4883-bc3c-25931fbea4ed/vAppRestorePoints" />       <Link Rel="Related" Type="RestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/33732b87-1074-4883-bc3c-25931fbea4ed/backupFiles" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

