---
title: "GET /agents/protectionGroups"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_agents_protectiongroups.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /agents/protectionGroups


Returns a resource representation of a collection of protection groups configured on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of protection groups, send the [GET /query?type=AgentProtectionGroup](get_query_agentprotectiongroup.md) request. |

Request

To get a list of protection groups, send the GET HTTP request to the /agents/protectionGroups resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/agents/protectionGroups |

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

In the response body, the REST API returns a representation of the /agents/protectionGroups resource.

Example

The example below returns a list of all protection groups on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/agents/protectionGroups  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:AgentProtectionGroup:1ca088be-7a63-43b9-bda1-2db2ad7a1bd5" Name="sql servers" Href="http://local.host:9399/api/agents/protectionGroups/1ca088be-7a63-43b9-bda1-2db2ad7a1bd5" Type="AgentProtectionGroupReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/protectionGroups/1ca088be-7a63-43b9-bda1-2db2ad7a1bd5?format=Entity" Name="sql servers" Type="AgentProtectionGroup" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/agents/protectionGroups/1ca088be-7a63-43b9-bda1-2db2ad7a1bd5/discoveredComputers" Type="DiscoveredComputerReferenceList" Rel="Down"/>     </Links>   </Ref>   <Ref UID="urn:veeam:AgentProtectionGroup:9093c50b-fc31-41e0-89d9-44c195a9eed5" Name="Protection Group" Href="http://local.host:9399/api/agents/protectionGroups/9093c50b-fc31-41e0-89d9-44c195a9eed5" Type="AgentProtectionGroupReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/protectionGroups/9093c50b-fc31-41e0-89d9-44c195a9eed5?format=Entity" Name="Protection Group" Type="AgentProtectionGroup" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/agents/protectionGroups/9093c50b-fc31-41e0-89d9-44c195a9eed5/discoveredComputers" Type="DiscoveredComputerReferenceList" Rel="Down"/>     </Links>   </Ref>   <Ref UID="urn:veeam:AgentProtectionGroup:8d8798d4-4911-4d80-b9d4-452629081648" Name="Manually Added" Href="http://local.host:9399/api/agents/protectionGroups/8d8798d4-4911-4d80-b9d4-452629081648" Type="AgentProtectionGroupReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/protectionGroups/8d8798d4-4911-4d80-b9d4-452629081648?format=Entity" Name="Manually Added" Type="AgentProtectionGroup" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/agents/protectionGroups/8d8798d4-4911-4d80-b9d4-452629081648/discoveredComputers" Type="DiscoveredComputerReferenceList" Rel="Down"/>     </Links>   </Ref>   <Ref UID="urn:veeam:AgentProtectionGroup:3cbecd3a-2df9-4a11-9e95-abcdf2d0e8a7" Name="Protection Group rhel 72 lvm" Href="http://local.host:9399/api/agents/protectionGroups/3cbecd3a-2df9-4a11-9e95-abcdf2d0e8a7" Type="AgentProtectionGroupReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/agents/protectionGroups/3cbecd3a-2df9-4a11-9e95-abcdf2d0e8a7?format=Entity" Name="Protection Group rhel 72 lvm" Type="AgentProtectionGroup" Rel="Alternate"/>       <Link Href="http://local.host:9399/api/agents/protectionGroups/3cbecd3a-2df9-4a11-9e95-abcdf2d0e8a7/discoveredComputers" Type="DiscoveredComputerReferenceList" Rel="Down"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

