---
title: "GET /agents/agentRestorePoints/{ID}/mounts"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_agents_agentrestorepoints_id_mounts.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# GET /agents/agentRestorePoints/{ID}/mounts


Returns a resource representation of a collection of mount points created for restore points of Veeam Agent machines.

Request

To get a list of mount points created for restore points of Veeam Agent machines, send the GET HTTP request to the /agents/agentRestorePoints/{ID}/mounts resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/agents/agentRestorePoints/{ID}/mounts |

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

In the response body, the REST API returns a representation of the /agents/agentRestorePoints/{ID}/mounts resource.

Example

The example below returns a list of Agent backup mount points for the restore point having ID fb87163e-687d-4006-96c9-0451b5423b85:

|  |
| --- |
| Request:  GET https://localhost:9398/api/agents/agentRestorePoints/fb87163e-687d-4006-96c9-0451b5423b85/mounts    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <AgentRestorePointMounts xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> |


