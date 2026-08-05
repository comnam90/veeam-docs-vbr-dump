---
title: "GET /backupServers"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_backupservers.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /backupServers


Returns a resource representation of a collection of all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of backup servers, send the [GET /query?type=BackupServer](get_query_backupserver.md) request. |

Request

To get a list of backup servers connected to Veeam Backup Enterprise Manager, send the GET HTTP request to the /backupServers resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/backupServers |

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

In the response body, the REST API returns a representation of the /backupServers resource collection.

Example

The example below returns a list of all backup servers that are currently connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/backupServers  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/1eb5b858-e557-43b3-8e79-386161b7ea44" Name="srv03.tech.local" UID="urn:veeam:BackupServer:1eb5b858-e557-43b3-8e79-386161b7ea44">     <Links>       <Link Rel="Down" Type="JobReferenceList" Href="https://localhost:9398/api/backupServers/1eb5b858-e557-43b3-8e79-386161b7ea44/jobs" />       <Link Rel="Down" Type="RepositoryReferenceList" Href="https://localhost:9398/api/backupServers/1eb5b858-e557-43b3-8e79-386161b7ea44/repositories" />       <Link Rel="Down" Type="CredentialsList" Href="https://localhost:9398/api/backupServers/1eb5b858-e557-43b3-8e79-386161b7ea44/credentials" />       <Link Rel="Down" Type="PasswordKeyList" Href="https://localhost:9398/api/backupServers/1eb5b858-e557-43b3-8e79-386161b7ea44/passwords" />       <Link Rel="Alternate" Type="BackupServer" Href="https://localhost:9398/api/backupServers/1eb5b858-e557-43b3-8e79-386161b7ea44?format=Entity" Name="srv03.tech.local" />       <Link Rel="Down" Type="ManagedServerReferenceList" Href="https://localhost:9398/api/backupServers/1eb5b858-e557-43b3-8e79-386161b7ea44/managedServers" />     </Links>   </Ref>   <Ref Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/6f17f70a-a61c-4ef0-ac7f-426a6ae1ec8b" Name="srv02.tech.local" UID="urn:veeam:BackupServer:6f17f70a-a61c-4ef0-ac7f-426a6ae1ec8b">     <Links>       <Link Rel="Down" Type="JobReferenceList" Href="https://localhost:9398/api/backupServers/6f17f70a-a61c-4ef0-ac7f-426a6ae1ec8b/jobs" />       <Link Rel="Down" Type="RepositoryReferenceList" Href="https://localhost:9398/api/backupServers/6f17f70a-a61c-4ef0-ac7f-426a6ae1ec8b/repositories" />       <Link Rel="Down" Type="CredentialsList" Href="https://localhost:9398/api/backupServers/6f17f70a-a61c-4ef0-ac7f-426a6ae1ec8b/credentials" />       <Link Rel="Down" Type="PasswordKeyList" Href="https://localhost:9398/api/backupServers/6f17f70a-a61c-4ef0-ac7f-426a6ae1ec8b/passwords" />       <Link Rel="Alternate" Type="BackupServer" Href="https://localhost:9398/api/backupServers/6f17f70a-a61c-4ef0-ac7f-426a6ae1ec8b?format=Entity" Name="srv02.tech.local" />       <Link Rel="Down" Type="ManagedServerReferenceList" Href="https://localhost:9398/api/backupServers/6f17f70a-a61c-4ef0-ac7f-426a6ae1ec8b/managedServers" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

