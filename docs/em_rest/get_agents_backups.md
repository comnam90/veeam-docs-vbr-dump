---
title: "GET /agents/backups"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_agents_backups.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /agents/backups


Returns a resource representation of a collection of all Veeam Agent backups on backup servers connected to Veeam Backup Enterprise Manager. The resource representation displays backups that were created by Veeam Agent managed by Veeam Backup & Replication. Backups of this type are also displayed in the representation of the [/backups](backups.md) resource collection.

Request

To get a list of Veeam Agent backups, send the GET HTTP request to the /agents/backups resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/agents/backups |

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

In the response body, the REST API returns a representation of the /agents/backups resource collection.

Example

The example below returns a list of all Veeam Agent backups on backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/agents/backups  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:Backup:437a5792-b83e-4fa7-ac14-0f5d7b9a4ead" Name="Agent Backup rhel72 lvm" Href="http://local.host:9399/api/backups/437a5792-b83e-4fa7-ac14-0f5d7b9a4ead" Type="BackupReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/repositories/44f0b2ba-9bff-4cd0-8d34-5b11e5d17fe9" Name="Scale-out Backup Repository" Type="RepositoryReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/437a5792-b83e-4fa7-ac14-0f5d7b9a4ead?format=Entity" Name="Agent Backup rhel72 lvm" Type="Backup" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backups/437a5792-b83e-4fa7-ac14-0f5d7b9a4ead/childbackups" Type="BackupReferenceList" Rel="Up"/>     </Links>   </Ref>   <Ref UID="urn:veeam:Backup:4ffe55d9-e431-4825-91e1-4a6ad404b5d6" Name="Agent Backup Policy 1 - srv02.local" Href="http://local.host:9399/api/backups/4ffe55d9-e431-4825-91e1-4a6ad404b5d6" Type="BackupReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/repositories/44f0b2ba-9bff-4cd0-8d34-5b11e5d17fe9" Name="Scale-out Backup Repository" Type="RepositoryReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/4ffe55d9-e431-4825-91e1-4a6ad404b5d6?format=Entity" Name="Agent Backup Policy 1 - srv02.local" Type="Backup" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backups/4ffe55d9-e431-4825-91e1-4a6ad404b5d6/restorePoints" Type="RestorePointReferenceList" Rel="Down"/>       <Link Href="http://local.host:9399/api/backups/f3c4a08c-f589-4c56-bd94-34705e91c40e" Name="Parent Backup" Type="BackupReference" Rel="Up"/>     </Links>   </Ref>   <Ref UID="urn:veeam:Backup:e9e2aa16-45ce-41ba-b5a4-4e1bdde078e2" Name="Backup Job AT12LIGHT" Href="http://local.host:9399/api/backups/e9e2aa16-45ce-41ba-b5a4-4e1bdde078e2" Type="BackupReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/repositories/8735f6ea-74f9-4337-9121-905fd427e7d0" Name="Default Backup Repository" Type="RepositoryReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/e9e2aa16-45ce-41ba-b5a4-4e1bdde078e2?format=Entity" Name="Backup Job AT12LIGHT" Type="Backup" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backups/e9e2aa16-45ce-41ba-b5a4-4e1bdde078e2/restorePoints" Type="RestorePointReferenceList" Rel="Down"/>     </Links>   </Ref>   <Ref UID="urn:veeam:Backup:f6307c50-934e-48ce-90a3-6ad0abe003bb" Name="Agent Backup Job SQL - sql12ten.local" Href="http://local.host:9399/api/backups/f6307c50-934e-48ce-90a3-6ad0abe003bb" Type="BackupReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/repositories/44f0b2ba-9bff-4cd0-8d34-5b11e5d17fe9" Name="Scale-out Backup Repository" Type="RepositoryReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/f6307c50-934e-48ce-90a3-6ad0abe003bb?format=Entity" Name="Agent Backup Job SQL - sql12ten.local" Type="Backup" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backups/f6307c50-934e-48ce-90a3-6ad0abe003bb/restorePoints" Type="RestorePointReferenceList" Rel="Down"/>       <Link Href="http://local.host:9399/api/backups/6148dc5b-7f92-4fd5-8d2a-e0ab86c2846c" Name="Parent Backup" Type="BackupReference" Rel="Up"/>     </Links>   </Ref>   <Ref UID="urn:veeam:Backup:8aafc7f2-a455-49a2-b66b-81d6f9b6ba2e" Name="Agent Backup rhel72 lvm - rhel72" Href="http://local.host:9399/api/backups/8aafc7f2-a455-49a2-b66b-81d6f9b6ba2e" Type="BackupReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/repositories/44f0b2ba-9bff-4cd0-8d34-5b11e5d17fe9" Name="Scale-out Backup Repository" Type="RepositoryReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/8aafc7f2-a455-49a2-b66b-81d6f9b6ba2e?format=Entity" Name="Agent Backup rhel72 lvm - rhel72" Type="Backup" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backups/8aafc7f2-a455-49a2-b66b-81d6f9b6ba2e/restorePoints" Type="RestorePointReferenceList" Rel="Down"/>       <Link Href="http://local.host:9399/api/backups/437a5792-b83e-4fa7-ac14-0f5d7b9a4ead" Name="Parent Backup" Type="BackupReference" Rel="Up"/>     </Links>   </Ref>   <Ref UID="urn:veeam:Backup:744414da-46a2-4341-83cb-c0c150a00369" Name="rhel72\_2025-12-12" Href="http://local.host:9399/api/backups/744414da-46a2-4341-83cb-c0c150a00369" Type="BackupReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/repositories/44f0b2ba-9bff-4cd0-8d34-5b11e5d17fe9" Name="Scale-out Backup Repository" Type="RepositoryReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/744414da-46a2-4341-83cb-c0c150a00369?format=Entity" Name="rhel72\_2025-12-12" Type="Backup" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backups/744414da-46a2-4341-83cb-c0c150a00369/restorePoints" Type="RestorePointReferenceList" Rel="Down"/>     </Links>   </Ref>   <Ref UID="urn:veeam:Backup:25338b6f-2c0b-4e03-b039-c200f62225e0" Name="Agent Backup Job SQL - sql2025.local" Href="http://local.host:9399/api/backups/25338b6f-2c0b-4e03-b039-c200f62225e0" Type="BackupReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/repositories/44f0b2ba-9bff-4cd0-8d34-5b11e5d17fe9" Name="Scale-out Backup Repository" Type="RepositoryReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/25338b6f-2c0b-4e03-b039-c200f62225e0?format=Entity" Name="Agent Backup Job SQL - sql2025.tech.local" Type="Backup" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backups/25338b6f-2c0b-4e03-b039-c200f62225e0/restorePoints" Type="RestorePointReferenceList" Rel="Down"/>       <Link Href="http://local.host:9399/api/backups/6148dc5b-7f92-4fd5-8d2a-e0ab86c2846c" Name="Parent Backup" Type="BackupReference" Rel="Up"/>     </Links>   </Ref>   <Ref UID="urn:veeam:Backup:6148dc5b-7f92-4fd5-8d2a-e0ab86c2846c" Name="Agent Backup Job SQL" Href="http://local.host:9399/api/backups/6148dc5b-7f92-4fd5-8d2a-e0ab86c2846c" Type="BackupReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/repositories/44f0b2ba-9bff-4cd0-8d34-5b11e5d17fe9" Name="Scale-out Backup Repository" Type="RepositoryReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backups/6148dc5b-7f92-4fd5-8d2a-e0ab86c2846c?format=Entity" Name="Agent Backup Job SQL" Type="Backup" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backups/6148dc5b-7f92-4fd5-8d2a-e0ab86c2846c/childbackups" Type="BackupReferenceList" Rel="Up"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

