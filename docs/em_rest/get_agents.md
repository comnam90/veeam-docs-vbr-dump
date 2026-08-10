---
title: "GET /agents"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_agents.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /agents


Returns a set of links to Veeam Agent Management resources.

Request

To get a list of Veeam Agent Management resources, send the GET HTTP request to the /agents resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/agents |

Request Header

The request contains the following headers:

Request Header

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

In the response body, the REST API returns a representation of the /agents resource.

Example

The example below returns a resource representation of the /agents resource.

|  |
| --- |
| Request:  GET https://localhost:9398/api/agents  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <Agents Href="http://local.host:9399/api/agents" Type="AgentsService" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Links>     <Link Href="http://local.host:9399/api/agents/jobs" Type="JobReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/agentRestorePoints" Type="AgentRestorePointReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/backups" Type="BackupReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/restorePoints" Type="RestorePointReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/backupFiles" Type="RestorePointReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/backupSessions" Type="BackupJobSessionReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/protectionGroups" Type="AgentProtectionGroupReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/discoveredComputers" Type="DiscoveredComputerReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/jobs?format=Entity" Type="JobList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/agentRestorePoints?format=Entity" Type="AgentRestorePointList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/backups?format=Entity" Type="BackupList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/restorePoints?format=Entity" Type="RestorePointList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/backupFiles?format=Entity" Type="RestorePointList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/backupSessions?format=Entity" Type="BackupJobSessionList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/protectionGroups?format=Entity" Type="AgentProtectionGroupList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/discoveredComputers?format=Entity" Type="DiscoveredComputerList" Rel="Down"/>   </Links> </Agents> |

Page updated 2026-07-29

