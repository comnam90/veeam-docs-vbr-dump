---
title: "GET /restorePoints/{ID}/backupFiles"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_restorepoints_id_backupfiles.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /restorePoints/{ID}/backupFiles


Returns a resource representation of a collection of backup files created for a restore point with the specified ID.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To get a list of backup files created for a specific restore point, send the GET HTTP request to the /restorePoints/{ID}/backupFiles resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/restorePoints/{ID}/backupFiles |

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

In the response body, the REST API returns a representation of the /restorePoints/{ID}/backupFiles resource collection.

Example

The example below returns a list of backup files created for the restore point with ID dc216c04-2e34-478e-8b9b-49a3397ef6f8.

|  |
| --- |
| Request:  GET https://localhost:9398/api/restorePoints/dc216c04-2e34-478e-8b9b-49a3397ef6f8/backupFiles  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/e86f61f9-4220-4f55-820b-e41a38abce90" Name="Oracle BackupD2025-10-06T165918.vib" UID="urn:veeam:BackupFile:e86f61f9-4220-4f55-820b-e41a38abce90">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/00fd67d9-2b4c-4c56-8a95-0b3dbec7ae43" Name="172.17.53.1" />       <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/61270417-d856-463f-abc4-b5ae70a2e1ab" Name="Oracle Backup" />       <Link Rel="Alternate" Type="BackupFile" Href="https://localhost:9398/api/backupFiles/e86f61f9-4220-4f55-820b-e41a38abce90?format=Entity" Name="Oracle BackupD2025-10-06T165918.vib" />       <Link Rel="Related" Type="BackupFileReferenceList" Href="https://localhost:9398/api/backupFiles/e86f61f9-4220-4f55-820b-e41a38abce90/restorePoints" />       <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/backupFiles/e86f61f9-4220-4f55-820b-e41a38abce90/vmRestorePoints" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

