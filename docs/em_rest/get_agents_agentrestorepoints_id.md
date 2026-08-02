---
title: "GET /agents/agentRestorePoints/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_agents_agentrestorepoints_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
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

In the response body, the REST API returns an entity or an entity reference of the /agents/agentRestorePoints/{ID} resource. The resource entity contains the following parameters and links.

Parameters

Response Body

| Element | Type | Description |
| UID | UidType | UID of the restore point resource, for example: urn:veeam:AgentRestorePoint:b6bfce60-7d42-46d7-9e55-0a40c04b0d7d. |
| Name | String | Name of the restore point, for example: sql01-hv@2025-08-24 05:03:25. |
| CreationTimeUTC | DateTime | Date and time when the restore point was created. The parameter accepts only UTC-formatted DateTime values. |
| Algorithm | String | Backup method used to create the restore point. Possible values:   * Full * Incremental * SyntheticFull |
| PointType | String | Type of the restore point. Possible values:   * Full * Increment |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=AgentRestorePoint](get_query_agentrestorepoint.md).

Links

Response Body

| Reference | Relationship | Description |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the Veeam Agent backup job was configured. |
| /restorePoints/{ID} | Up | URL of the [/restorePoints/{ID}](restorepoints_id.md) resource — a parent restore point. |
| /backupFiles/{ID} | Up | URL of the [/backupFiles/{ID}](backupfiles_id.md) resource — a backup file created for the Veeam Agent restore point. |
| /agents/agentRestorePoints/{ID} | Alternate | Alternate URL of the [/agents/agentRestorePoints/{ID}](agents_agentrestorepoints_id.md) resource. |
| /agents/agentRestorePoints/{ID}/mounts | Down | URL of the [/agents/agentRestorePoints/{ID}/mounts](agents_agentrestorepoints_id_mounts.md) resource — a collection of mount points created for the Veeam Agent restore point. |

Example

The example below returns a restore point having ID b6bfce60-7d42-46d7-9e55-0a40c04b0d7d for the rhel72 VM:

|  |
| --- |
| Request:  GET https://localhost:9398/api/agents/agentRestorePoints/b6bfce60-7d42-46d7-9e55-0a40c04b0d7d  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <AgentRestorePoint Href="http://local.host:9399/api/agents/agentRestorePoints/b6bfce60-7d42-46d7-9e55-0a40c04b0d7d?format=Entity" Type="AgentRestorePoint" Name="rhel72@2025-12-17 02:01:05" UID="urn:veeam:AgentRestorePoint:b6bfce60-7d42-46d7-9e55-0a40c04b0d7d" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Links>     <Link Href="http://local.host:9399/api/backupServers/8c88c6d6-931f-4044-8c0b-7a0c5f188b00" Name="local.host" Type="BackupServerReference" Rel="Up"/>     <Link Href="http://local.host:9399/api/restorePoints/67e4d9b0-a461-41e6-b5e8-037af89e2a88" Name="Dec 17 2025  2:00AM" Type="RestorePointReference" Rel="Up"/>     <Link Href="http://local.host:9399/api/backupFiles/0e2f90e9-23ee-43fe-8279-d0220b081da2" Name="Agent Backup rhel72 lvm - rhel72\_2D7FD2025-12-17T050032.vib" Type="BackupFileReference" Rel="Up"/>     <Link Href="http://local.host:9399/api/agents/agentRestorePoints/b6bfce60-7d42-46d7-9e55-0a40c04b0d7d" Name="rhel72@2025-12-17 02:01:05" Type="AgentRestorePointReference" Rel="Alternate"/>     <Link Href="http://local.host:9399/api/agents/agentRestorePoints/b6bfce60-7d42-46d7-9e55-0a40c04b0d7d/mounts" Type="AgentRestorePointMountList" Rel="Down"/>     <Link Href="http://local.host:9399/api/agents/agentRestorePoints/b6bfce60-7d42-46d7-9e55-0a40c04b0d7d/mounts" Type="AgentRestorePointMount" Rel="Create"/>   </Links>   <CreationTimeUTC>2025-12-17T02:01:05Z</CreationTimeUTC>   <Algorithm>Incremental</Algorithm>   <PointType>Increment</PointType> </AgentRestorePoint> |

Page updated 2026-07-29

