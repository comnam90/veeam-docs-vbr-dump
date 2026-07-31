---
title: "GET /managedServers"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_managedservers.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /managedServers


Returns a resource representation of a collection of all servers connected to backup servers that are managed by Veeam Backup Enterprise Manager.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of managed servers, send the [GET /query?type=ManagedServer](get_query_managedserver.md) request. |

Request

To get a list of servers connected to backup servers, send the GET HTTP request to the /managedServers resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/managedServers |

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

In the response body, the REST API returns a representation of the /managedServers resource collection.

Example

The example below returns a list of all servers that are currently connected to backup servers managed by Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/managedServers  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="ManagedServerReference" Href="https://localhost:9398/api/managedServers/0d7ea80c-6ac8-46bf-863c-3a6093f8baec" Name="vc01" UID="urn:veeam:ManagedServer:0d7ea80c-6ac8-46bf-863c-3a6093f8baec">     <Links>       <Link Rel="Alternate" Type="ManagedServer" Href="https://localhost:9398/api/managedServers/0d7ea80c-6ac8-46bf-863c-3a6093f8baec?format=Entity" Name="vc01" />       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02" />     </Links>   </Ref>   <Ref Type="ManagedServerReference" Href="https://localhost:9398/api/managedServers/a5352877-3b99-4e2a-8700-400cb3eefb56" Name="172.16.16.77" UID="urn:veeam:ManagedServer:a5352877-3b99-4e2a-8700-400cb3eefb56">     <Links>       <Link Rel="Alternate" Type="ManagedServer" Href="https://localhost:9398/api/managedServers/a5352877-3b99-4e2a-8700-400cb3eefb56?format=Entity" Name="172.16.16.77" />       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02" />     </Links>   </Ref>   <Ref Type="ManagedServerReference" Href="https://localhost:9398/api/managedServers/5b133853-b0cf-4bb6-8c11-4f9dcb258b26" Name="172.16.13.45" UID="urn:veeam:ManagedServer:5b133853-b0cf-4bb6-8c11-4f9dcb258b26">     <Links>       <Link Rel="Alternate" Type="ManagedServer" Href="https://localhost:9398/api/managedServers/5b133853-b0cf-4bb6-8c11-4f9dcb258b26?format=Entity" Name="172.16.13.45" />       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02" />     </Links>   </Ref>   <Ref Type="ManagedServerReference" Href="https://localhost:9398/api/managedServers/5b768a76-bcc1-48ed-af47-85424cc43584" Name="172.16.1.102" UID="urn:veeam:ManagedServer:5b768a76-bcc1-48ed-af47-85424cc43584">     <Links>       <Link Rel="Alternate" Type="ManagedServer" Href="https://localhost:9398/api/managedServers/5b768a76-bcc1-48ed-af47-85424cc43584?format=Entity" Name="172.16.1.102" />       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02" />     </Links>   </Ref>  </EntityReferences> |

Page updated 2026-07-29

