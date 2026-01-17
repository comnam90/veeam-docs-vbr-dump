---
title: "GET /agents/discoveredComputers/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_agents_discoveredcomputers_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# GET /agents/discoveredComputers/{ID}


Returns a resource representation of a protected computer having the specified ID.

Request

To get a job session, send the GET HTTP request to the /agents/discoveredComputers/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/agents/discoveredComputers/{ID} |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
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

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns an entity or an entity reference of the /agents/discoveredComputers/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the protected computer, for example: urn:veeam:DiscoveredComputer:b85df3d1-c094-437c-b836-eaca6c3762ca. |
| Name | String | Name of the protected computer, for example: AgentProtected.local. |
| HostStatus | String | Status of the host:   * Online * Offline |
| AgentVersion | String | Version of Veeam Agent installed on the protected computer. |
| AgentStatus | String | Veeam Agent installation status:   * NotInstalled * Installed * UnsupportedOs * Failed * Exclude |
| OsVersion | String | Version of the OS installed on the protected computer. |
| IpAddress | String | IP address of the protected computer. |
| HierarchyObjRef | HierarchyObjRefType | Reference to the protected computer. |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=DiscoveredComputer](get_query_discoveredcomputer.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the protection group was created. |
| /agents/discoveredComputers/{ID} | Alternate | Alternate URL of the [/agents/discoveredComputers/{ID}](agents_discoveredcomputers_id.md) resource. |
| /agents/protectionGroups/{ID} | Down | URL of the [/agents/protectionGroups/{ID}](agents_protectiongroups_id.md) resource — a protection group that contains the discovered computer. |

Example

An example below returns an entity representation of the protected computer resource having ID b85df3d1-c094-437c-b836-eaca6c3762ca.

|  |
| --- |
| Request:  GET https://localhost:9398/api/agents/discoveredComputers/b85df3d1-c094-437c-b836-eaca6c3762ca?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <DiscoveredComputer xmlns="http://www.veeam.com/ent/v1.0" Type="DiscoveredComputer" Href="https://localhost:9398/api/backupTaskSessions/b85df3d1-c094-437c-b836-eaca6c3762ca?format=Entity" Name="enterprise03.tech.local" UID="urn:veeam:DiscoveredComputer:b85df3d1-c094-437c-b836-eaca6c3762ca"> |


