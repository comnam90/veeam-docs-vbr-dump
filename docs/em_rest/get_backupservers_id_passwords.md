---
title: "GET /backupServers/{ID}/passwords"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_backupservers_id_passwords.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /backupServers/{ID}/passwords


Returns a resource representation of the passwords collection created on the backup server with the specified ID.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of passwords, send the [GET /query?type=Passwords](get_query_passwords.md) request. |

Request

To get a list of passwords created on a specific backup server, send the GET HTTP request to the /backupServers/{ID}/passwords resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/backupServers/{ID}/passwords |

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

In the response body, the REST API returns a representation of the /backupServers/{ID}/passwords resource collection.

Example

The example below returns a list of all passwords created on the backup server having ID 50a1b2fb-b90a-4e05-816f-e298eb2f995c.

|  |
| --- |
| Request:  GET https://localhost:9398/api/backupServers/50a1b2fb-b90a-4e05-816f-e298eb2f995c/passwords  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <PasswordKeyInfoList xmlns="http://www.veeam.com/ent/v1.0">   <PasswordKeyInfo Type="PasswordKey" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018/passwords/cacd84ea-5cc9-46b5-9e79-2162c4170662">     <Links>       <Link Rel="Up" Type="BackupServer" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018?format=Entity" Name="srv02.tech.local" />       <Link Rel="Edit" Type="PasswordKey" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018/passwords/cacd84ea-5cc9-46b5-9e79-2162c4170662" />       <Link Rel="Delete" Type="PasswordKey" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018/passwords/cacd84ea-5cc9-46b5-9e79-2162c4170662" />     </Links>     <Id>cacd84ea-5cc9-46b5-9e79-2162c4170662</Id>     <Hint>My password</Hint>     <LastModificationDate>2025-10-10T23:06:17-08:00</LastModificationDate>   </PasswordKeyInfo>   <PasswordKeyInfo Type="PasswordKey" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018/passwords/3b39fed1-c9e8-46bf-be7e-2a096a210341">     <Links>       <Link Rel="Up" Type="BackupServer" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018?format=Entity" Name="srv02.tech.local" />       <Link Rel="Edit" Type="PasswordKey" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018/passwords/3b39fed1-c9e8-46bf-be7e-2a096a210341" />       <Link Rel="Delete" Type="PasswordKey" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018/passwords/3b39fed1-c9e8-46bf-be7e-2a096a210341" />     </Links>     <Id>3b39fed1-c9e8-46bf-be7e-2a096a210341</Id>     <Hint>My favorite book</Hint>     <LastModificationDate>2025-10-13T02:50:38-07:00</LastModificationDate>   </PasswordKeyInfo> </PasswordKeyInfoList> |

Page updated 2026-07-29

