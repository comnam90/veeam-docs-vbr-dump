---
title: "GET /agents/discoveredComputers"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_agents_discoveredcomputers.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /agents/discoveredComputers


Returns a resource representation of a collection of all protected computers in protection groups configured on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of protected computers, send the [GET /query?type=AgentProtectionGroup](get_query_agentprotectiongroup.md) request. |

Request

To get a list of all protected computers, send the GET HTTP request to the /agents/discoveredComputers resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/agents/discoveredComputers |

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

In the response body, the REST API returns a representation of the /agents/discoveredComputers resource.

Example

The example below returns a list of all protected computers on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/agents/discoveredComputers  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:DiscoveredComputer:b0ad8ec4-5f17-45e6-be9b-1334ea320af0" Name="win7x86.local" Href="http://local.host:9399/api/backupTaskSessions/b0ad8ec4-5f17-45e6-be9b-1334ea320af0" Type="DiscoveredComputerReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/discoveredComputers/b0ad8ec4-5f17-45e6-be9b-1334ea320af0?format=Entity" Name="win7x86.local" Type="DiscoveredComputer" Rel="Alternate"/>     </Links>   </Ref>   <Ref UID="urn:veeam:DiscoveredComputer:9ee13ff9-aaa7-403d-80c1-9f49833b90a9" Name="sql12ten.local" Href="http://local.host:9399/api/backupTaskSessions/9ee13ff9-aaa7-403d-80c1-9f49833b90a9" Type="DiscoveredComputerReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/discoveredComputers/9ee13ff9-aaa7-403d-80c1-9f49833b90a9?format=Entity" Name="sql12ten.tech.local" Type="DiscoveredComputer" Rel="Alternate"/>     </Links>   </Ref>   <Ref UID="urn:veeam:DiscoveredComputer:53518661-b43f-4e50-a8cf-cffead274366" Name="rhel72" Href="http://local.host:9399/api/backupTaskSessions/53518661-b43f-4e50-a8cf-cffead274366" Type="DiscoveredComputerReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/discoveredComputers/53518661-b43f-4e50-a8cf-cffead274366?format=Entity" Name="rhel72" Type="DiscoveredComputer" Rel="Alternate"/>     </Links>   </Ref>   <Ref UID="urn:veeam:DiscoveredComputer:53518661-b43f-4e50-a8cf-cffead274366" Name="rhel72" Href="http://local.host:9399/api/backupTaskSessions/53518661-b43f-4e50-a8cf-cffead274366" Type="DiscoveredComputerReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/discoveredComputers/53518661-b43f-4e50-a8cf-cffead274366?format=Entity" Name="rhel72" Type="DiscoveredComputer" Rel="Alternate"/>     </Links>   </Ref>   <Ref UID="urn:veeam:DiscoveredComputer:a2db19ca-200f-4231-b655-ec47651cecb9" Name="sql2025.local" Href="http://local.host:9399/api/backupTaskSessions/a2db19ca-200f-4231-b655-ec47651cecb9" Type="DiscoveredComputerReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/discoveredComputers/a2db19ca-200f-4231-b655-ec47651cecb9?format=Entity" Name="sql2025.local" Type="DiscoveredComputer" Rel="Alternate"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

