---
title: "GET /query?type=AgentRestorePoint"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_agentrestorepoint.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a collection of restore points for separate machines in Veeam Agent backups. For details, see [/agents/agentRestorePoints](agents_agentrestorepoints.md).

Request

To get a list of restore points for separate machines protected with Veeam Agent, send the GET HTTP request to the query with the type parameter set to AgentRestorePoint.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=AgentRestorePoint |

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
| UID | UidType | UID of the Veeam Agent restore point resource. |
| Name | String | Name of the Veeam Agent restore point, for example: sql01-hv@2013-08-24 05:03:25. |
| CreationTime | DateTime | Date and time when the restore point was created. The parameter accepts only UTC-formatted DateTime values. |
| ComputerName | String | Name of the machine protected with Veeam Agent for which the restore point has been created. |
| Type | String | Type of the restore point. Possible values:   * Full * Increment |
| Algorithm | String | Backup method used to create the restore point. Possible values:   * Full * Incremental * SyntheticFull |
| RestorePointId | UidType | UID of the restore point. |
| RestorePointName | String | Name of the restore point. |
| BackupUid | UidType | UID of the machine backup parent to the restore point resource. |
| BackupName | String | Name of the backup parent to the restore point resource. |
| BackupFileUid | UidType | UID of the backup file created for the Veeam Agent restore point. |
| BackupFileName | String | Name of the backup file created for the Veeam Agent restore point. |
| BackupServerUid | UidType | UID of the backup server on which the restore point has been created. |
| BackupServerName | String | Name of the backup server on which the restore point has been created. |

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

In the response body, the REST API returns a representation of the /agents/agentRestorePoints resource collection.

Example

The example below returns an entity resource representation of a collection of full restore points created by Agent backup jobs.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=AgentRestorePoint&format=Entities&filter=Type==Full    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
