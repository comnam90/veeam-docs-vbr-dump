---
title: "get_query_passwords"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_passwords.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a collection of passwords created on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/backupServers/{ID}/passwords](backupservers_id_passwords.md).

Request

To get a list of passwords, send the GET HTTP request to the query with the type parameter set to Passwords.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=Passwords |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Optional Parameters

In the query, you can use the following parameters for filtering.

| Parameter | Type | Description |
| --- | --- | --- |
| PasswordKeyID | String | ID of the password created on the backup server, for example: bd2fe652-b6c0-4f9f-b466-e10c4dc3e3da |
| Hint | String | Hint for the password. |
| BackupServerUid | UidType | UID of the backup server where the password has been created, for example: urn:veeam:BackupServer:15942270-fb56-4dcc-96e9-5f80e4725a15. |
| BackupServerName | String | Name of the backup server where the password has been created. |

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

In the response body, the REST API returns a representation of the /backupServers/{ID}/passwords resource collection.

Example

The example below returns an entity resource representation of a collection of passwords created on the enterprise06.tech.local backup server.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=Passwords&format=Entities&filter=BackupServerName=="enterprise06.tech.local"    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
