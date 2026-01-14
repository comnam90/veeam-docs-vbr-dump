---
title: "get_backupservers_id_creds"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_backupservers_id_creds.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of the credentials collection created on the backup server with the specified ID.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of credentials, send the [GET /query?type=Credentials](get_query_credentials.md) request. |

Request

To get a list of credentials created on a specific backup server, send the GET HTTP request to the /backupServers/{ID}/credentials resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/backupServers/{ID}/credentials |

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

In the response body, the REST API returns a representation of the /backupServers/{ID}/credentials resource collection.

Example

The example below returns a list of all credentials created on the backup server having ID 50a1b2fb-b90a-4e05-816f-e298eb2f995c.

|  |
| --- |
| Request:  GET https://localhost:9398/api/backupServers/50a1b2fb-b90a-4e05-816f-e298eb2f995c/credentials    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <CredentialsInfoList xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
