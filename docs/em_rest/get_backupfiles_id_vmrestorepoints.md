---
title: "GET /backupFiles/{ID}/vmRestorePoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_backupfiles_id_vmrestorepoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /backupFiles/{ID}/vmRestorePoints


Returns a collection of restore points for separate VMs in a backup file with the specified ID. The backup file was created on or imported to the backup server connected to Veeam Backup Enterprise Manager.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To get a collection of restore points for separate VMs in a backup file, send the GET HTTP request to the /backupFiles/{ID}/vmRestorePoints resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/backupFiles/{ID}/vmRestorePoints |

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

In the response body, the REST API returns a representation of the /backupFiles/{ID}/vmRestorePoints resource.

Example

The example below returns a collection of restore points for separate VMs in a backup file with ID 98c2ba69-16b8-4162-80a4-c6ba1a2ff02c.

|  |
| --- |
| Request:  GET https://localhost:9398/api/backupFiles/98c2ba69-16b8-4162-80a4-c6ba1a2ff02c/vmRestorePoints  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/657351ca-e263-4127-8748-99ba1bd76ee4" Name="apache03@2025-09-21 15:04:45" UID="urn:veeam:VmRestorePoint:657351ca-e263-4127-8748-99ba1bd76ee4">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/99f01406-ecdc-428f-ae09-a13de244140a" Name="172.17.53.1" />       <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/cf5bf1e1-f551-4e67-95d1-fee4370aa733" Name="Sep 21 2025  3:03PM" />       <Link Rel="Up" Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/98c2ba69-16b8-4162-80a4-c6ba1a2ff02c" Name="Webserver BackupD2025-09-21T180331.vib" />       <Link Rel="Alternate" Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/657351ca-e263-4127-8748-99ba1bd76ee4?format=Entity" Name="apache03@2025-09-21 15:04:45" />     </Links>   </Ref>   <Ref Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/8189ee7a-6cb2-43f8-b238-e2e417993727" Name="websrv02@2025-09-21 15:04:45" UID="urn:veeam:VmRestorePoint:8189ee7a-6cb2-43f8-b238-e2e417993727">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/99f01406-ecdc-428f-ae09-a13de244140a" Name="172.17.53.1" />       <Link Rel="Up" Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/cf5bf1e1-f551-4e67-95d1-fee4370aa733" Name="Sep 21 2025  3:03PM" />       <Link Rel="Up" Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/98c2ba69-16b8-4162-80a4-c6ba1a2ff02c" Name="Webserver BackupD2025-09-21T180331.vib" />       <Link Rel="Alternate" Type="VmRestorePoint" Href="https://localhost:9398/api/vmRestorePoints/8189ee7a-6cb2-43f8-b238-e2e417993727?format=Entity" Name="websrv02@2025-09-21 15:04:45" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

