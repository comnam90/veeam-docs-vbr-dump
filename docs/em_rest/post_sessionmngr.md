---
title: "POST /sessionMngr/"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_sessionmngr.html"
last_updated: "9/26/2025"
product_version: "13.0.1.1071"
---

# POST /sessionMngr/


Creates a new logon session for Veeam Backup Enterprise Manager REST API.

Request

To create a new logon session, send the POST HTTP request to the /sessionMngr/ resource.

|  |
| --- |
| Note |
| To work with Veeam Backup Enterprise Manager REST API resources available in the current version of Veeam Backup & Replication and to access a complete set of actions that can be performed with those resources, create a new logon session using the link to the latest version of the /sessionMngr/ resource. For details, see [Perform Logon](logging_on.md). |

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/sessionMngr/?v=v1\_7 |

or

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/sessionMngr/?v=latest |

Request Header

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

|  |
| --- |
| Note |
| To create a new logon session for a tenant, you need to provide tenant credentials in the request body. For details, see [Tenant Logon Session](cloud_connect_tenant_credentials.md). |

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 201 Created.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns a resource representation of the created logon session. The resource representation of the logon session contains links to resources available through Veeam Backup Enterprise Manager REST API.

Example

The example below creates a new logon session for Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Request:  POST https://localhost:9398/api/sessionMngr/?v=v1\_7    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Request Body:  None    Response:  201 Created    Response Body:  <LogonSession xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0" Href="https://enterprise04.tech.local:9398/api/logonSessions/7686d89e-26fd-48e6-963c-c9dbce802981" Type="LogonSession"> |


