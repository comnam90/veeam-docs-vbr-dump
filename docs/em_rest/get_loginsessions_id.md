---
title: "GET /logonSessions/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_loginsessions_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# GET /logonSessions/{ID}


Returns a currently existing logon session having the specified ID.

Request

To get a logon session having the specified ID, send the GET HTTP request to the /logonSessions/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/logonSessions/{ID} |

Request Header

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

In the response body, the REST API returns a representation of the /logonSessions/{ID} resource that contains the following parameters as well as links of resources available for the user account used for creating the logon session.

| Element | Type | Description |
| --- | --- | --- |
| UserName | String | User name of the account used for the logon session, for example: ENTERPRISE04\Administrator. |
| SessionId | String | Id of the logon session, for example: d7e68afd-cc15-4b1a-bd30-51eb309a1dab. |

Example

The example below returns a logon session created for Veeam Backup Enterprise Manager REST API. The logon session has ID 5496707f-c814-47ce-8d6d-110aa03cec03:

|  |
| --- |
| Request:  GET https://localhost:9398/api/logonSessions/5496707f-c814-47ce-8d6d-110aa03cec03    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <LogonSession xmlns="http://www.veeam.com/ent/v1.0" Type="LogonSession" Href="https://localhost:9398/api/logonSessions/5496707f-c814-47ce-8d6d-110aa03cec03"> |


