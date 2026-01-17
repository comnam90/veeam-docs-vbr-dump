---
title: "GET /agents/agentRestorePoints/{ID}/mounts/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_agents_agentrestorepoints_id_mounts_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a mount point having the specified ID. The mount point was created for a restore point of a Veeam Agent machine.

Request

To get a specific mount point, send the GET HTTP request to the /agents/agentRestorePoints/{ID}/mounts/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/agents/agentRestorePoints/{ID}/mounts/{ID} |

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

In the response body, the REST API returns the /agents/agentRestorePoints/{ID}/mounts/{ID} resource representation that contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| FSRoots | DirectoryEntryListType | Collection of DirectoryEntry resources that represent guest OS files and folders in the machine file system hierarchy. For details, see [Directory Entries](#DirectoryEntries). |

Directory Entries

The DirectoryEntry resource contains the following parameters.

| Element | Type | Description |
| --- | --- | --- |
| Path | String | Path to the directory entry in the machine file system hierarchy, for example: C:\Shares. |
| Name | String | Name of the directory entry, for example: Shares. |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /agents/agentRestorePoints/{ID}/mounts/{ID} | Delete | URL for the [DELETE /agents/agentRestorePoints/{ID}/mounts/{ID}](delete_agents_agentrestorepoints_id_mounts_id.md) request. |

Example

The example below returns a resource representation of the mount point having ID 1 for the machine restore point having ID dd3cf3d0-0533-424e-abc3-249c4c62b797:

|  |
| --- |
| Request:  GET https://localhost:9398/api/agents/agentRestorePoints/dd3cf3d0-0533-424e-abc3-249c4c62b797/mounts/1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <AgentRestorePointMount Href="https://localhost:9398/api/agents/agentRestorePoints/dd3cf3d0-0533-424e-abc3-249c4c62b797/mounts/1" Type="AgentRestorePointMount" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
