---
title: "GET /restorePoints/{ID}/vmRestorePoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_restorepoints_id_vmrestorepoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /restorePoints/{ID}/vmRestorePoints


Returns a resource representation of a collection of restore points for separate VMs created for a backup restore point with the specified ID.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To get a list of restore points for separate VMs created for a specific restore point, send the GET HTTP request to the /restorePoints/{ID}/vmRestorePoints resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/restorePoints/{ID}/vmRestorePoints |

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

In the response body, the REST API returns a representation of the /restorePoints/{ID}/vmRestorePoints resource collection.

Example

The example below returns a list of restore points for separate VMs created for the restore point with ID dc216c04-2e34-478e-8b9b-49a3397ef6f8.

|  |
| --- |
| Request:  GET https://localhost:9398/api/restorePoints/dc216c04-2e34-478e-8b9b-49a3397ef6f8/vmRestorePoints  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/5acac742-ee17-4080-8e89-a6ea67adfcf3" Name="oracle03@2025-10-06 13:59:50" UID="urn:veeam:VmRestorePoint:5acac742-ee17-4080-8e89-a6ea67adfcf3">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/00fd67d9-2b4c-4c56-8a95-0b3dbec7ae43" Name="172.17.53.1" />       <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/dc216c04-2e34-478e-8b9b-49a3397ef6f8" Name="Oct  6 2025  1:59PM" />       <Link Rel="Up" Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/e86f61f9-4220-4f55-820b-e41a38abce90" Name="Oracle BackupD2025-10-06T165918.vib" />       <Link Rel="Alternate" Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/5acac742-ee17-4080-8e89-a6ea67adfcf3?format=Entity" Name="oracle03@2025-10-06 13:59:50" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

