---
title: "put_backupservers_id_passwords_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/put_backupservers_id_passwords_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Edits parameters for a password having the specified ID on the backup server with the specified ID.

Request

To edit parameters for the password, send the PUT HTTP request to the /backupServers/{ID}/passwords/{ID} resource.

HTTP Request

|  |
| --- |
| PUT https://<Enterprise-Manager>:9398/api/backupServers/{ID}/passwords/{ID} |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters for the password that must be updated on the backup server. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Note |
| Currently, the only parameter that can be edited for the password is the Hint parameter. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Hint | String | Hint for the password. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "Hint": "My password"  } |

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 204 No Content.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

None.

Example

The example below updates the hint parameter in the password having ID c473b8df-4499-41b8-ba6b-7f76def6fea1 on the backup server with ID f62624c1-8462-4747-8bd4-d686f99b0540.

|  |
| --- |
| Request:  PUT https://localhost:9398/api/backupServers/f62624c1-8462-4747-8bd4-d686f99b0540/passwords/c473b8df-4499-41b8-ba6b-7f76def6fea1    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <PasswordKeyInfoSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Hint>My password</Hint> </PasswordKeyInfoSpec>    Response:  204 No Content |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
