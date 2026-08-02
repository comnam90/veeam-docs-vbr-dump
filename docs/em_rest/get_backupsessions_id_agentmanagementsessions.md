---
title: "GET /backupSessions/{ID}/agentManagementSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_backupsessions_id_agentmanagementsessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /backupSessions/{ID}/agentManagementSessions


Returns a resource representation of a collection of all [AgentManagement](get_backupsessions_id.md#JobType) job sessions performed during the [AgentBackup](get_backupsessions_id.md#JobType) backup session with a specified ID. Note, the request only returns the sessions that has been created for the last 30 days.

Supported Platforms

The request is supported for Veeam Agent computers running Microsoft Windows or Linux.

Request

To get a list of all AgentManagement sessions in AgentBackup job session, send the GET HTTP request to the /backupSessions/{ID}/agentManagementSessions resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/backupSessions/{ID}/agentManagementSessions |

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

In the response body, the REST API returns a representation of the /backupSessions/{ID}/agentManagementSessions resource.

Example

The example below returns a list of sessions for Veeam Agent backup jobs performed during a backup session with an ID 8ba90554-4cb0-4979-b4cc-00887fcd1caa.

|  |
| --- |
| Request:  GET https://localhost:9398/api/backupSessions/8ba90554-4cb0-4979-b4cc-00887fcd1caa/agentManagementSessions  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:BackupJobSession:0e6b4c7d-0d9c-4ab9-94a7-71e39895485b" Name="Agent Backup Job SQL - sql12ten.local@2025-12-20 14:30:45" Href="http://local.host:9399/api/backupSessions/0e6b4c7d-0d9c-4ab9-94a7-71e39895485b" Type="BackupJobSessionReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/jobs/77dc8834-2102-4edf-8a0d-aba909b2d1ed" Name="Agent Backup Job SQL - sql12ten.local" Type="JobReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupSessions/8ba90554-4cb0-4979-b4cc-00887fcd1caa" Name="Parent session" Type="BackupJobSessionReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupSessions/0e6b4c7d-0d9c-4ab9-94a7-71e39895485b?format=Entity" Name="Agent Backup Job SQL - sql12ten.local@2025-12-20 14:30:45" Type="BackupJobSession" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backupSessions/0e6b4c7d-0d9c-4ab9-94a7-71e39895485b/taskSessions" Type="BackupTaskSessionReferenceList" Rel="Down"/>     </Links>   </Ref>   <Ref UID="urn:veeam:BackupJobSession:b66c1ef7-290a-4646-a34b-df28813df301" Name="Agent Backup Job SQL - sql2025.local@2025-12-20 14:30:45" Href="http://local.host:9399/api/backupSessions/b66c1ef7-290a-4646-a34b-df28813df301" Type="BackupJobSessionReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/jobs/abd14f39-6fc0-4e79-b777-96126c62fdd3" Name="Agent Backup Job SQL - sql2025.local" Type="JobReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupSessions/8ba90554-4cb0-4979-b4cc-00887fcd1caa" Name="Parent session" Type="BackupJobSessionReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/backupSessions/b66c1ef7-290a-4646-a34b-df28813df301?format=Entity" Name="Agent Backup Job SQL - sql2025.local@2025-12-20 14:30:45" Type="BackupJobSession" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/backupSessions/b66c1ef7-290a-4646-a34b-df28813df301/taskSessions" Type="BackupTaskSessionReferenceList" Rel="Down"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-28

