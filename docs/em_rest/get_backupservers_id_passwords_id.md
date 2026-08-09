---
title: "GET /backupServers/{ID}/passwords/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_backupservers_id_passwords_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /backupServers/{ID}/passwords/{ID}


Returns a resource representation of a password with the specified ID created on the backup server with the specified ID.

Request

To get a resource representation of the password created on a specific backup server, send the GET HTTP request to the /backupServers/{ID}/passwords/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/backupServers/{ID}/passwords/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /backupServers/{ID}/passwords/{ID} resource. The resource entity contains the following parameters and links.

Parameters

Response Body

| Element | Type | Description |
| ID | String | ID of the password created on the backup server, for example: bd2fe652-b6c0-4f9f-b466-e10c4dc3e3da |
| Hint | String | Hint for the password. |
| LastModificationDate | DateTime | Date and time when the password was last modified. |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=Passwords](get_query_passwords.md).

Links

Response Body

| Reference | Relationship | Description |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the password has been created. |
| /backupServers/{ID}/passwords/{ID} | Edit | Alternate URL of the [PUT /backupServers/{ID}/passwords/{ID}](put_backupservers_id_passwords_id.md) resource. |
| /backupServers/{ID}/passwords/{ID} | Delete | URL for the [DELETE /backupServers/{ID}/passwords/{ID}](delete_backupservers_id_passwords_id.md) request. |

Example

The example below returns a password having ID 6d63bbc8-1daf-4992-8577-88b63739dd8e created on the backup server having ID a490c017-2c1c-40ee-8bcf-73bcce6ab36f.

|  |
| --- |
| Request:  GET https://localhost:9398/api/backupServers/a490c017-2c1c-40ee-8bcf-73bcce6ab36f/passwords/6d63bbc8-1daf-4992-8577-88b63739dd8e  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <?xml version="1.0" encoding="utf-8"?> <PasswordKeyInfo xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" Href="https://localhost:9398/api/backupServers/a490c017-2c1c-40ee-8bcf-73bcce6ab36f/passwords/6d63bbc8-1daf-4992-8577-88b63739dd8e" Type="PasswordKey" xmlns="http://www.veeam.com/ent/v1.0">     <Links>         <Link Href="https://localhost:9398/api/backupServers/a490c017-2c1c-40ee-8bcf-73bcce6ab36f?format=Entity" Name="enterprise01.tech.local" Type="BackupServer" Rel="Up" />         <Link Href="https://localhost:9398/api/backupServers/a490c017-2c1c-40ee-8bcf-73bcce6ab36f/passwords/6d63bbc8-1daf-4992-8577-88b63739dd8e" Type="PasswordKey" Rel="Edit" />         <Link Href="https://localhost:9398/api/backupServers/a490c017-2c1c-40ee-8bcf-73bcce6ab36f/passwords/6d63bbc8-1daf-4992-8577-88b63739dd8e" Type="PasswordKey" Rel="Delete" />     </Links>     <Id>6d63bbc8-1daf-4992-8577-88b63739dd8e</Id>     <Hint>Standard</Hint>     <LastModificationDate>2025-09-03T15:01:14+02:00</LastModificationDate> </PasswordKeyInfo> |

Page updated 2026-07-29

