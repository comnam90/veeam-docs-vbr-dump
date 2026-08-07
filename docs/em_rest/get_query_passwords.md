---
title: "GET /query?type=Passwords"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_passwords.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=Passwords


Returns a resource representation of a collection of passwords created on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/backupServers/{ID}/passwords](backupservers_id_passwords.md).

Request

To get a list of passwords, send the GET HTTP request to the query with the type parameter set to Passwords.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=Passwords |

Request Headers

The request contains the following headers:

Request Headers

| Header | Required | Description |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Optional Parameters

In the query, you can use the following parameters for filtering.

Optional Parameters

| Parameter | Type | Description |
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

Response Headers

| Header | Description |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns a representation of the /backupServers/{ID}/passwords resource collection.

Example

The example below returns an entity resource representation of a collection of passwords created on the enterprise06.tech.local backup server.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=Passwords&format=Entities&filter=BackupServerName=="enterprise06.tech.local"  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Resources>     <PasswordKeyInfoList>       <PasswordKeyInfo Type="PasswordKey" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563/passwords/ebf6c20f-7126-4186-a1b8-24e6c541161c">         <Links>           <Link Rel="Up" Type="BackupServer" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563?format=Entity" Name="enterprise06.tech.local" />           <Link Rel="Edit" Type="PasswordKey" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563/passwords/ebf6c20f-7126-4186-a1b8-24e6c541161c" />           <Link Rel="Delete" Type="PasswordKey" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563/passwords/ebf6c20f-7126-4186-a1b8-24e6c541161c" />         </Links>         <Id>ebf6c20f-7126-4186-a1b8-24e6c541161c</Id>         <Hint>Admin password</Hint>         <LastModificationDate>2025-06-24T21:04:18+02:00</LastModificationDate>       </PasswordKeyInfo>       <PasswordKeyInfo Type="PasswordKey" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563/passwords/45376db8-eb62-4940-8c4d-c6adf0ca11a1">         <Links>           <Link Rel="Up" Type="BackupServer" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563?format=Entity" Name="enterprise06.tech.local" />           <Link Rel="Edit" Type="PasswordKey" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563/passwords/45376db8-eb62-4940-8c4d-c6adf0ca11a1" />           <Link Rel="Delete" Type="PasswordKey" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563/passwords/45376db8-eb62-4940-8c4d-c6adf0ca11a1" />         </Links>         <Id>45376db8-eb62-4940-8c4d-c6adf0ca11a1</Id>         <Hint>Lorem ipsum dolor sit amet</Hint>         <LastModificationDate>2025-06-24T21:05:56+02:00</LastModificationDate>       </PasswordKeyInfo>     </PasswordKeyInfoList>   </Resources>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=Passwords&format=Entities&filter=BackupServerName=="enterprise06.tech.local"&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=Passwords&format=Entities&filter=BackupServerName=="enterprise06.tech.local"&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

