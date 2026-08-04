---
title: "GET /agents/agentRestorePoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_agents_agentrestorepoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /agents/agentRestorePoints


Returns a resource representation of a collection of restore points for separate machines in Veeam Agent backups. Backups are created by Veeam Agent managed by Veeam Backup & Replication.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of the restore points for separate machines in Veeam Agent backups, send the [GET /query?type=AgentRestorePoint](get_query_agentrestorepoint.md) request. |

Request

To get a list of restore points for separate machines protected with Veeam Agent managed by Veeam Backup & Replication, send the GET HTTP request to the /agents/agentRestorePoints resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/agents/agentRestorePoints |

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

In the response body, the REST API returns a representation of the /agents/agentRestorePoints resource collection.

Example

The example below returns a list of all restore points for Veeam Agent backups on backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/agents/agentRestorePoints  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:AgentRestorePoint:f7807556-1001-4875-9736-02fff650ca22" Name="sql12ten.local@2025-12-18 03:02:29" Href="http://local.host:9399/api/agents/agentRestorePoints/f7807556-1001-4875-9736-02fff650ca22" Type="AgentRestorePointReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/3e1e451a-4718-4475-836b-9547ccae6872" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/restorePoints/7a783889-61d4-4ccb-8ea4-dce7ff2799ce" Name="Dec 18 2025  3:01AM" Type="RestorePointReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupFiles/06bc03eb-a6cd-4bb5-8cde-eec6da37ab79" Name="Agent Backup Job SQL - sql12ten.veea\_7500D2025-12-18T060109.vib" Type="BackupFileReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/agentRestorePoints/f7807556-1001-4875-9736-02fff650ca22?format=Entity" Name="sql12ten.local@2025-12-18 03:02:29" Type="AgentRestorePoint" Rel="Alternate"/>     </Links>   </Ref>   <Ref UID="urn:veeam:AgentRestorePoint:0b64039c-cc71-49d1-bb17-03aac684195b" Name="sql12ten.local@2025-12-16 01:01:09" Href="http://local.host:9399/api/agents/agentRestorePoints/0b64039c-cc71-49d1-bb17-03aac684195b" Type="AgentRestorePointReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/3e1e451a-4718-4475-836b-9547ccae6872" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/restorePoints/96d06451-e3f8-4e84-a654-8d8cde618994" Name="Dec 16 2025  1:00AM" Type="RestorePointReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupFiles/21b6dffe-ff1f-4fc6-98ce-263640531154" Name="Agent Backup Job SQL - sql12ten.veea\_EBB8D2025-12-16T040044.vib" Type="BackupFileReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/agentRestorePoints/0b64039c-cc71-49d1-bb17-03aac684195b?format=Entity" Name="sql12ten.local@2025-12-16 01:01:09" Type="AgentRestorePoint" Rel="Alternate"/>     </Links>   </Ref>   <Ref UID="urn:veeam:AgentRestorePoint:117fe4ab-33ff-4254-900b-084d5c7b1afb" Name="sql12ten.local@2025-12-19 05:02:56" Href="http://local.host:9399/api/agents/agentRestorePoints/117fe4ab-33ff-4254-900b-084d5c7b1afb" Type="AgentRestorePointReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/3e1e451a-4718-4475-836b-9547ccae6872" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/restorePoints/711adce7-ef22-4c5f-92f6-37aa9b9644ec" Name="Dec 19 2025  5:01AM" Type="RestorePointReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupFiles/bc20e231-6b3b-4c1e-ab87-a776e7cd4dcb" Name="Agent Backup Job SQL - sql12ten.veea\_2FD2D2025-12-19T080119.vib" Type="BackupFileReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/agentRestorePoints/117fe4ab-33ff-4254-900b-084d5c7b1afb?format=Entity" Name="sql12ten.local@2025-12-19 05:02:56" Type="AgentRestorePoint" Rel="Alternate"/>     </Links>   </Ref>   <Ref UID="urn:veeam:AgentRestorePoint:90e83c3f-4d9c-4596-b745-09a7657f1157" Name="sql12ten.local@2025-12-17 21:02:25" Href="http://local.host:9399/api/agents/agentRestorePoints/90e83c3f-4d9c-4596-b745-09a7657f1157" Type="AgentRestorePointReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/3e1e451a-4718-4475-836b-9547ccae6872" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/restorePoints/44a8ccd8-ddb7-454c-8210-21c238c0dbe4" Name="Dec 17 2025  9:01PM" Type="RestorePointReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupFiles/a222e9e6-155b-4f71-bfa3-8740470da8d5" Name="Agent Backup Job SQL - sql12ten.veea\_4224D2025-12-18T000110.vib" Type="BackupFileReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/agentRestorePoints/90e83c3f-4d9c-4596-b745-09a7657f1157?format=Entity" Name="sql12ten.local@2025-12-17 21:02:25" Type="AgentRestorePoint" Rel="Alternate"/>     </Links>   </Ref>   ... </EntityReferences> |

Page updated 2026-07-29

