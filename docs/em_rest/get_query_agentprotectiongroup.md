---
title: "GET /query?type=AgentProtectionGroup"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_agentprotectiongroup.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=AgentProtectionGroup


Returns a resource representation of a collection of protection groups configured on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/agents/protectionGroups](agents_protectiongroups.md).

Request

To get a list of protection groups, send the GET HTTP request to the query with the type parameter set to AgentProtectionGroup.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=AgentProtectionGroup |

Request Headers

The request contains the following headers:

Request Headers

| Header | Required | Description |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Optional Parameters

In the query, you can use the following parameters for filtering and sorting.

Optional Parameters

| Parameter | Type | Description |
| UID | UidType | UID of a protection group, for example: 88b395e2-81ff-439c-558c-188d97274c15. |
| Name | String | Name of a protection group, for example: Agent Protection Group. |
| BackupServerUid | UidType | UID of the backup server parent to the protection group resource. |
| BackupServerName | String | Name of the backup server parent to the protection group resource. |

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

In the response body, the REST API returns a representation of the /agents/protectionGroups resource collection.

Example

The example below returns an entity resource representation of a collection of protection groups configured on the backup server that has ID 445e6ce-86f5-4171-b909-dac209c66563.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=AgentProtectionGroup&format=Entities&filter=BackupServerUid==7445e6ce-86f5-4171-b909-dac209c66563  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <AgentProtectionGroups>       <AgentProtectionGroup Type="AgentProtectionGroup" Href="https://localhost:9398/api/agents/protectionGroups/032acd33-2896-43c2-b1b9-7bd39ac77543?format=Entity" Name="Manually Added" UID="urn:veeam:AgentProtectionGroup:032acd33-2896-43c2-b1b9-7bd39ac77543">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Alternate" Type="AgentProtectionGroupReference" Href="https://localhost:9398/api/agents/protectionGroups/032acd33-2896-43c2-b1b9-7bd39ac77543" Name="Manually Added" />           <Link Rel="Down" Type="DiscoveredComputerList" Href="https://localhost:9398/api/agents/protectionGroups/032acd33-2896-43c2-b1b9-7bd39ac77543/discoveredComputers?format=Entity" />         </Links>         <RescanScheduleEnabled>true</RescanScheduleEnabled>         <HierarchyObjRef>urn:AgentForWindows:AgentProtectionGroup:00000000-0000-0000-0000-000000000000.730dc485-84c2-4a9d-86e7-2e35d1d5a0be</HierarchyObjRef>       </AgentProtectionGroup>       <AgentProtectionGroup Type="AgentProtectionGroup" Href="https://localhost:9398/api/agents/protectionGroups/d0671b61-8f92-45a7-a199-ab2aad8037c6?format=Entity" Name="Protection Group 1" UID="urn:veeam:AgentProtectionGroup:d0671b61-8f92-45a7-a199-ab2aad8037c6">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Alternate" Type="AgentProtectionGroupReference" Href="https://localhost:9398/api/agents/protectionGroups/d0671b61-8f92-45a7-a199-ab2aad8037c6" Name="Protection Group 1" />           <Link Rel="Down" Type="DiscoveredComputerList" Href="https://localhost:9398/api/agents/protectionGroups/d0671b61-8f92-45a7-a199-ab2aad8037c6/discoveredComputers?format=Entity" />         </Links>         <RescanScheduleEnabled>true</RescanScheduleEnabled>         <HierarchyObjRef>urn:AgentForWindows:AgentProtectionGroup:00000000-0000-0000-0000-000000000000.400c385e-8a97-4d37-bac5-e6a2266a9ee5</HierarchyObjRef>       </AgentProtectionGroup>     </AgentProtectionGroups>   </Entities>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=AgentProtectionGroup&format=Entities&filter=BackupServerUid==7445e6ce-86f5-4171-b909-dac209c66563&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=AgentProtectionGroup&format=Entities&filter=BackupServerUid==7445e6ce-86f5-4171-b909-dac209c66563&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

