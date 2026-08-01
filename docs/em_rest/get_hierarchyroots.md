---
title: "GET /hierarchyRoots"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_hierarchyroots.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /hierarchyRoots


Returns a resource representation of a collection of virtualization hosts added to all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of virtualization hosts, send the [GET /query?type=HierarchyRoot](get_query_hierarchyroot.md) request. |

Request

To get a list of virtualization hosts, send the GET HTTP request to the /hierarchyRoots resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/hierarchyRoots |

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

In the response body, the REST API returns a representation of the /hierarchyRoots resource collection.

Example

The example below returns a list of all virtualization hosts added to backup servers that are connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/hierarchyRoots  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="HierarchyRootReference" Href="https://localhost:9398/api/hierarchyRoots/0d7ea80c-6ac8-46bf-863c-3a6093f8baec" Name="vc01" UID="urn:veeam:HierarchyRoot:0d7ea80c-6ac8-46bf-863c-3a6093f8baec">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="HierarchyRoot" Href="https://localhost:9398/api/hierarchyRoots/0d7ea80c-6ac8-46bf-863c-3a6093f8baec?format=Entity" Name="vcdev51" />     </Links>   </Ref>   <Ref Type="HierarchyRootReference" Href="https://localhost:9398/api/hierarchyRoots/15410946-fc21-4b82-a53a-717478eae90f" Name="172.16.13.45" UID="urn:veeam:HierarchyRoot:15410946-fc21-4b82-a53a-717478eae90f">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="HierarchyRoot" Href="https://localhost:9398/api/hierarchyRoots/15410946-fc21-4b82-a53a-717478eae90f?format=Entity" Name="172.16.13.45" />     </Links>   </Ref>   <Ref Type="HierarchyRootReference" Href="https://localhost:9398/api/hierarchyRoots/9f591b3b-0072-4326-9bcc-9dabb4218df5" Name="172.16.21.1" UID="urn:veeam:HierarchyRoot:9f591b3b-0072-4326-9bcc-9dabb4218df5">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="HierarchyRoot" Href="https://localhost:9398/api/hierarchyRoots/9f591b3b-0072-4326-9bcc-9dabb4218df5?format=Entity" Name="172.16.21.1" />     </Links>   </Ref>   <Ref Type="HierarchyRootReference" Href="https://localhost:9398/api/hierarchyRoots/d63a6e79-e771-4c77-80be-ad7b6edc2ba7" Name="172.16.1.57" UID="urn:veeam:HierarchyRoot:d63a6e79-e771-4c77-80be-ad7b6edc2ba7">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="HierarchyRoot" Href="https://localhost:9398/api/hierarchyRoots/d63a6e79-e771-4c77-80be-ad7b6edc2ba7?format=Entity" Name="172.16.1.57" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

