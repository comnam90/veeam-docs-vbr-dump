---
title: "GET /restorePoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_restorepoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /restorePoints


Returns a resource representation of a restore points collection for backups and replicas created on or imported to backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of restore points, send the [GET /query?type=RestorePoint](get_query_restorepoint.md) request. |

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To get a list of restore points, send the GET HTTP request to the /restorePoints resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/restorePoints |

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

In the response body, the REST API returns a representation of the /restorePoints resource collection.

Example

The example below returns a list of all restore points for backups and replicas created on or imported to backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/restorePoints  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/391bd194-fcf4-4ce3-a507-27447bc0a4cd" Name="Oct  9 2025  7:07AM" UID="urn:veeam:RestorePoint:391bd194-fcf4-4ce3-a507-27447bc0a4cd">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/c19136d3-2eb1-4032-b56f-38ff7e630470" Name="Oracle Backup\_imported" />       <Link Rel="Alternate" Type="RestorePoint" Href="https://localhost:9398/api/restorePoints/391bd194-fcf4-4ce3-a507-27447bc0a4cd?format=Entity" Name="Oct  9 2025  7:07AM" />       <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/391bd194-fcf4-4ce3-a507-27447bc0a4cd/vmRestorePoints" />       <Link Rel="Down" Type="VAppRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/391bd194-fcf4-4ce3-a507-27447bc0a4cd/vAppRestorePoints" />       <Link Rel="Related" Type="RestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/391bd194-fcf4-4ce3-a507-27447bc0a4cd/backupFiles" />     </Links>   </Ref>   <Ref Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/2b70d451-5a99-48f2-ab6f-336fd7a112fb" Name="Oct  5 2025  8:26AM" UID="urn:veeam:RestorePoint:2b70d451-5a99-48f2-ab6f-336fd7a112fb">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/ef3bd23f-c284-44bc-abcb-1e03e150f2c6" Name="Webserver Backup" />       <Link Rel="Alternate" Type="RestorePoint" Href="https://localhost:9398/api/restorePoints/2b70d451-5a99-48f2-ab6f-336fd7a112fb?format=Entity" Name="Oct  5 2025  8:26AM" />       <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/2b70d451-5a99-48f2-ab6f-336fd7a112fb/vmRestorePoints" />       <Link Rel="Down" Type="VAppRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/2b70d451-5a99-48f2-ab6f-336fd7a112fb/vAppRestorePoints" />       <Link Rel="Related" Type="RestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/2b70d451-5a99-48f2-ab6f-336fd7a112fb/backupFiles" />     </Links>   </Ref>   <Ref Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/e4108a85-4532-4b1a-b1b6-3c1faba1c4de" Name="Oct  6 2025  1:06PM" UID="urn:veeam:RestorePoint:e4108a85-4532-4b1a-b1b6-3c1faba1c4de">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/ef3bd23f-c284-44bc-abcb-1e03e150f2c6" Name="Webserver Backup" />       <Link Rel="Alternate" Type="RestorePoint" Href="https://localhost:9398/api/restorePoints/e4108a85-4532-4b1a-b1b6-3c1faba1c4de?format=Entity" Name="Oct  6 2025  1:06PM" />       <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/e4108a85-4532-4b1a-b1b6-3c1faba1c4de/vmRestorePoints" />       <Link Rel="Down" Type="VAppRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/e4108a85-4532-4b1a-b1b6-3c1faba1c4de/vAppRestorePoints" />       <Link Rel="Related" Type="RestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/e4108a85-4532-4b1a-b1b6-3c1faba1c4de/backupFiles" />     </Links>   </Ref>   <Ref Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/9dad9b51-436c-4730-811a-64c542711a93" Name="Oct  6 2025  1:06PM" UID="urn:veeam:RestorePoint:9dad9b51-436c-4730-811a-64c542711a93">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/4bb923d9-749d-423b-aa76-a72fda2f2ade" Name="Mediaserver Backup" />       <Link Rel="Alternate" Type="RestorePoint" Href="https://localhost:9398/api/restorePoints/9dad9b51-436c-4730-811a-64c542711a93?format=Entity" Name="Oct  6 2025  1:06PM" />       <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/9dad9b51-436c-4730-811a-64c542711a93/vmRestorePoints" />       <Link Rel="Down" Type="VAppRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/9dad9b51-436c-4730-811a-64c542711a93/vAppRestorePoints" />       <Link Rel="Related" Type="RestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/9dad9b51-436c-4730-811a-64c542711a93/backupFiles" />     </Links>   </Ref>   <Ref Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/ea2fe574-91b9-486b-8256-8d6e767aacdb" Name="Oct 18 2025  1:09PM" UID="urn:veeam:RestorePoint:ea2fe574-91b9-486b-8256-8d6e767aacdb">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/d5311600-78a5-48d3-8e69-0fed4d3b5744" Name="Oracle Backup" />       <Link Rel="Alternate" Type="RestorePoint" Href="https://localhost:9398/api/restorePoints/ea2fe574-91b9-486b-8256-8d6e767aacdb?format=Entity" Name="Oct 18 2025  1:09PM" />       <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/ea2fe574-91b9-486b-8256-8d6e767aacdb/vmRestorePoints" />       <Link Rel="Down" Type="VAppRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/ea2fe574-91b9-486b-8256-8d6e767aacdb/vAppRestorePoints" />       <Link Rel="Related" Type="RestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/ea2fe574-91b9-486b-8256-8d6e767aacdb/backupFiles" />     </Links>   </Ref>   <Ref Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/ca884aee-3646-4880-98ae-9b30c33a79b7" Name="Oct 10 2025  7:46AM" UID="urn:veeam:RestorePoint:ca884aee-3646-4880-98ae-9b30c33a79b7">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/21bef8b5-8030-4886-ab6d-b445c34a831d" Name="Daily Job 01" />       <Link Rel="Alternate" Type="RestorePoint" Href="https://localhost:9398/api/restorePoints/ca884aee-3646-4880-98ae-9b30c33a79b7?format=Entity" Name="Oct 10 2025  7:46AM" />       <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/ca884aee-3646-4880-98ae-9b30c33a79b7/vmRestorePoints" />       <Link Rel="Down" Type="VAppRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/ca884aee-3646-4880-98ae-9b30c33a79b7/vAppRestorePoints" />       <Link Rel="Related" Type="RestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/ca884aee-3646-4880-98ae-9b30c33a79b7/backupFiles" />     </Links>   </Ref>   <Ref Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/09a3bd4d-7d34-47f2-89e4-b050841dd393" Name="Oct 13 2025  9:51AM" UID="urn:veeam:RestorePoint:09a3bd4d-7d34-47f2-89e4-b050841dd393">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/76eaa065-a210-466a-bc89-6c68d7d40c20" Name="SQL Backup" />       <Link Rel="Alternate" Type="RestorePoint" Href="https://localhost:9398/api/restorePoints/09a3bd4d-7d34-47f2-89e4-b050841dd393?format=Entity" Name="Oct 13 2025  9:51AM" />       <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/09a3bd4d-7d34-47f2-89e4-b050841dd393/vmRestorePoints" />       <Link Rel="Down" Type="VAppRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/09a3bd4d-7d34-47f2-89e4-b050841dd393/vAppRestorePoints" />       <Link Rel="Related" Type="RestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/09a3bd4d-7d34-47f2-89e4-b050841dd393/backupFiles" />     </Links>   </Ref>   <Ref Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/a398100b-8b07-436f-b2e7-d92804a49625" Name="Oct  5 2025  8:28AM" UID="urn:veeam:RestorePoint:a398100b-8b07-436f-b2e7-d92804a49625">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/4bb923d9-749d-423b-aa76-a72fda2f2ade" Name="Mediaserver Backup" />       <Link Rel="Alternate" Type="RestorePoint" Href="https://localhost:9398/api/restorePoints/a398100b-8b07-436f-b2e7-d92804a49625?format=Entity" Name="Oct  5 2025  8:28AM" />       <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/a398100b-8b07-436f-b2e7-d92804a49625/vmRestorePoints" />       <Link Rel="Down" Type="VAppRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/a398100b-8b07-436f-b2e7-d92804a49625/vAppRestorePoints" />       <Link Rel="Related" Type="RestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/a398100b-8b07-436f-b2e7-d92804a49625/backupFiles" />     </Links>   </Ref>   <Ref Type="RestorePointReference" Href="https://localhost:9398/api/restorePoints/0a3adbad-74b7-4db2-ba76-e091e0332114" Name="Oct 13 2025  9:45AM" UID="urn:veeam:RestorePoint:0a3adbad-74b7-4db2-ba76-e091e0332114">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="BackupReference" Href="https://localhost:9398/api/backups/76eaa065-a210-466a-bc89-6c68d7d40c20" Name="SQL Backup" />       <Link Rel="Alternate" Type="RestorePoint" Href="https://localhost:9398/api/restorePoints/0a3adbad-74b7-4db2-ba76-e091e0332114?format=Entity" Name="Oct 13 2025  9:45AM" />       <Link Rel="Down" Type="VmRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/0a3adbad-74b7-4db2-ba76-e091e0332114/vmRestorePoints" />       <Link Rel="Down" Type="VAppRestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/0a3adbad-74b7-4db2-ba76-e091e0332114/vAppRestorePoints" />       <Link Rel="Related" Type="RestorePointReferenceList" Href="https://localhost:9398/api/restorePoints/0a3adbad-74b7-4db2-ba76-e091e0332114/backupFiles" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

