---
title: "GET /agents/agentRestorePoints/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_agents_agentrestorepoints_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# GET /agents/agentRestorePoints/{ID}


Returns a resource representation of a restore point having the specified ID. A restore point was created for a machine protected with Veeam Agent managed by Veeam Backup & Replication.

Request

To get a restore point created for a machine protected with Veeam Agent, send the GET HTTP request to the /agents/agentRestorePoints/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/agents/agentRestorePoints/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /agents/agentRestorePoints/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the restore point resource, for example: urn:veeam:AgentRestorePoint:b6bfce60-7d42-46d7-9e55-0a40c04b0d7d. |
| Name | String | Name of the restore point, for example: sql01-hv@2013-08-24 05:03:25. |
| CreationTimeUTC | DateTime | Date and time when the restore point was created. The parameter accepts only UTC-formatted DateTime values. |
| Algorithm | String | Backup method used to create the restore point. Possible values:   * Full * Incremental * SyntheticFull |
| PointType | String | Type of the restore point. Possible values:   * Full * Increment |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=AgentRestorePoint](get_query_agentrestorepoint.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the Veeam Agent backup job was configured. |
| /restorePoints/{ID} | Up | URL of the [/restorePoints/{ID}](restorepoints_id.md) resource — a parent restore point. |
| /backupFiles/{ID} | Up | URL of the [/backupFiles/{ID}](backupfiles_id.md) resource — a backup file created for the Veeam Agent restore point. |
| /agents/agentRestorePoints/{ID} | Alternate | Alternate URL of the [/agents/agentRestorePoints/{ID}](agents_agentrestorepoints_id.md) resource. |
| /agents/agentRestorePoints/{ID}/mounts | Down | URL of the [/agents/agentRestorePoints/{ID}/mounts](agents_agentrestorepoints_id_mounts.md) resource — a collection of mount points created for the Veeam Agent restore point. |

Example

The example below returns a restore point having ID b6bfce60-7d42-46d7-9e55-0a40c04b0d7d for the rhel72 VM:

|  |
| --- |
| Request:  GET https://localhost:9398/api/agents/agentRestorePoints/b6bfce60-7d42-46d7-9e55-0a40c04b0d7d    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <AgentRestorePoint Href="http://local.host:9399/api/agents/agentRestorePoints/b6bfce60-7d42-46d7-9e55-0a40c04b0d7d?format=Entity" Type="AgentRestorePoint" Name="rhel72@2018-12-17 02:01:05" UID="urn:veeam:AgentRestorePoint:b6bfce60-7d42-46d7-9e55-0a40c04b0d7d" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> |


