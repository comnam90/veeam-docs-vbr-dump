---
title: "GET /nas/fileServers"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_nas_fileservers.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /nas/fileServers


Returns a resource representation of a collection of file shares added on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of file shares, send the [GET /query?type=FileServer](get_query_fileserver.md) request. |

Request

To get a list of file shares added on all backup servers connected to Veeam Backup Enterprise Manager, send the GET HTTP request to the /nas/fileServers resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/nas/fileServers |

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

In the response body, the REST API returns a representation of the /nas/fileServers resource collection.

Example

The example below returns a list of all file shares added on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/nas/fileServers  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="FileServerReference" Href="https://srv12.tech.local:9398/api/repositories/517be4c8-9c43-4e7c-9f59-4e368d3a8f3c" Name="\\srv12\share" UID="urn:veeam:FileServer:517be4c8-9c43-4e7c-9f59-4e368d3a8f3c">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />       <Link Rel="Alternate" Type="FileServer" Href="https://srv12.tech.local:9398/api/nas/fileServers/517be4c8-9c43-4e7c-9f59-4e368d3a8f3c?format=Entity" Name="\\srv12\share" />     </Links>   </Ref>   <Ref Type="FileServerReference" Href="https://srv12.tech.local:9398/api/repositories/c407ce33-0d08-4aac-8cc0-e28c055ae3bc" Name="172.24.30.115:/home/veeam" UID="urn:veeam:FileServer:c407ce33-0d08-4aac-8cc0-e28c055ae3bc">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://srv12.tech.local:9398/api/backupServers/d1444f74-27e6-4399-81a9-d28ba98913f0" Name="srv12.tech.local" />       <Link Rel="Alternate" Type="FileServer" Href="https://srv12.tech.local:9398/api/nas/fileServers/c407ce33-0d08-4aac-8cc0-e28c055ae3bc?format=Entity" Name="172.24.30.115:/home/veeam" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

