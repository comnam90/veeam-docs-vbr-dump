---
title: "GET /query?type=DiscoveredComputer"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_discoveredcomputer.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# GET /query?type=DiscoveredComputer


Returns a resource representation of a collection of protected computers in protection groups configured on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/agents/discoveredComputers](agents_discoveredcomputers.md).

Request

To get a list of protected computers, send the GET HTTP request to the query with the type parameter set to DiscoveredComputer.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=DiscoveredComputer |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Optional Parameters

In the query, you can use the following parameters for filtering and sorting.

| Parameter | Type | Description |
| --- | --- | --- |
| UID | String | ID of a protected computer, for example: 88b395e2-81ff-439c-558c-188d97274c15. |
| Name | String | Name of a protected computer, for example: AgentProtected.local. |
| BackupServerUid | UidType | UID of the backup server parent to the protected computer resource. |
| BackupServerName | String | Name of the backup server parent to the protected computer resource. |
| AgentVersion | String | Version of Veeam Agent installed on the protected computer. |
| AgentStatus | String | Veeam Agent installation status:   * NotInstalled * Installed * UnsupportedOs * Failed * Exclude |
| OsVersion | String | Version of the OS installed on the protected computer. |
| IpAddress | String | IP address of the protected computer. |
| ProtectionGroupUid | UidType | UID of a protection group that contains the protected computer. |
| ProtectionGroupName | String | Name of a protection group that contains the protected computer. |

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

In the response body, the REST API returns a representation of the /agents/discoveredComputers resource collection.

Example

The example below returns an entity resource representation of a discovered computer that has IP address 172.17.53.55.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=DiscoveredComputer&format=Entities&filter=IpAddress=="172.17.53.55"    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |


