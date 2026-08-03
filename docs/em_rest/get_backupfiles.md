---
title: "GET /backupFiles"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_backupfiles.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /backupFiles


Returns a resource representation of a collection of backup files created on or imported to backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of backup sessions, send the [GET /query?type=BackupFile](get_query_backupfile.md) request. |

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To get a list of backup files, send the GET HTTP request to the /backupFiles resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/backupFiles |

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

In the response body, the REST API returns a representation of the /backupFiles resource collection.

Example

The example below returns a list of all backup files created on backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/backupFiles  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4" Name="Webserver Backup CopyD2025-09-20T000000.vbk" UID="urn:veeam:BackupFile:6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/99f01406-ecdc-428f-ae09-a13de244140a" Name="172.17.53.1" />       <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/80672bda-76a8-408b-947f-afd0ff67fba6" Name="Webserver Backup Copy" />       <Link Rel="Alternate" Type="BackupFile" Href="https://localhost:9398/api/backupFiles/6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4?format=Entity" Name="Webserver Backup CopyD2025-09-20T000000.vbk" />       <Link Rel="Related" Type="BackupFileReferenceList" Href="https://localhost:9398/api/backupFiles/6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4/restorePoints" />       <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/backupFiles/6ed26dc7-cc9e-4a89-9226-1ed9996fb1f4/vmRestorePoints" />     </Links>   </Ref>   <Ref Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/0874ab95-10e5-4f25-84df-2782ad81f3e5" Name="Webserver BackupD2025-09-20T175902.vib" UID="urn:veeam:BackupFile:0874ab95-10e5-4f25-84df-2782ad81f3e5">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/99f01406-ecdc-428f-ae09-a13de244140a" Name="172.17.53.1" />       <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/10cf7239-ddbd-47ad-8cfa-15438a5a5467" Name="Webserver Backup" />       <Link Rel="Alternate" Type="BackupFile" Href="https://localhost:9398/api/backupFiles/0874ab95-10e5-4f25-84df-2782ad81f3e5?format=Entity" Name="Webserver BackupD2025-09-20T175902.vib" />       <Link Rel="Related" Type="BackupFileReferenceList" Href="https://localhost:9398/api/backupFiles/0874ab95-10e5-4f25-84df-2782ad81f3e5/restorePoints" />       <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/backupFiles/0874ab95-10e5-4f25-84df-2782ad81f3e5/vmRestorePoints" />     </Links>   </Ref>   <Ref Type="BackupFileReference" Href="https://localhost:9398/api/backupFiles/312ab2fc-69c5-4bb4-af9b-910064d34313" Name="Webserver BackupD2025-09-20T175525.vbk" UID="urn:veeam:BackupFile:312ab2fc-69c5-4bb4-af9b-910064d34313">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/99f01406-ecdc-428f-ae09-a13de244140a" Name="172.17.53.1" />       <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/10cf7239-ddbd-47ad-8cfa-15438a5a5467" Name="Webserver Backup" />       <Link Rel="Alternate" Type="BackupFile" Href="https://localhost:9398/api/backupFiles/312ab2fc-69c5-4bb4-af9b-910064d34313?format=Entity" Name="Webserver BackupD2025-09-20T175525.vbk" />       <Link Rel="Related" Type="BackupFileReferenceList" Href="https://localhost:9398/api/backupFiles/312ab2fc-69c5-4bb4-af9b-910064d34313/restorePoints" />       <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/backupFiles/312ab2fc-69c5-4bb4-af9b-910064d34313/vmRestorePoints" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

