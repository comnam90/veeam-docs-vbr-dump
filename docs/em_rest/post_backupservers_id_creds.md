---
title: "POST /backupServers/{ID}/credentials?action=create"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_backupservers_id_creds.html"
last_updated: "3/1/2024"
product_version: "13.0.1.1071"
---


In this article

Creates new credentials on the backup server having the specified ID.

Request

To create new credentials record on a specific backup server, send the POST HTTP request to the /backupServers/{ID}/credentials?action=create URL.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/backupServers/{ID}/credentials?action=create |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters for the new credentials record that must be created on the backup server. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Username | String | User name of the added credentials record in the DOMAIN\USENAME format. | Yes | 0/1 |
| Description | String | Description of the added credentials record. | Yes | 0/1 |
| Password | String | Password of the added credentials. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "Username": "VEEAM\\Administrator",   "Description": "Created with REST API",   "Password": "1234"  } |

Response

The server returns the following response to the client.

Response Codes

A successfully operation returns response code 201 Created.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

None.

Example

The example below adds a new credentials record on the backup server having ID f62624c1-8462-4747-8bd4-d686f99b0540. The credentials have the following parameters:

* User name VEEAM\Administrator
* Password 1234
* Description Credentials created with REST API

|  |
| --- |
| Request:  POST https://localhost:9398/api/backupServers/f62624c1-8462-4747-8bd4-d686f99b0540/credentials?action=create    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <CredentialsInfoSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Username>VEEAM\Administrator</Username>   <Description>Credentials created with REST API</Description>   <Password>1234</Password> </CredentialsInfoSpec>    Response:  201 Created    Response Body:  None |

Page updated 3/1/2024

Page content applies to build 13.0.1.1071
