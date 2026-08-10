---
title: "GET /restoreSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_restoresessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /restoreSessions


Returns a collection of restore sessions performed on all backup servers connected to Veeam Backup Enterprise Manager. Note, the request only returns the sessions that has been created for the last 30 days.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of restore sessions, send the [GET /query?type=RestoreSession](get_query_restoresession.md) request. |

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To get a list of restore sessions, send the GET HTTP request to the /restoreSessions resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/restoreSessions |

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

In the response body, the REST API returns a representation of the /restoreSessions resource.

Example

The example below returns a resource collection listing all restore sessions performed on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/restoreSessions  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="RestoreSessionReference" Href="https://localhost:9398/api/restoreSessions/676dc837-f441-4ac1-8470-15be06b4cffc" Name="FLR\_[srv04]@2025-10-19 05:59:18" UID="urn:veeam:RestoreSession:676dc837-f441-4ac1-8470-15be06b4cffc">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="RestoreSession" Href="https://localhost:9398/api/restoreSessions/676dc837-f441-4ac1-8470-15be06b4cffc?format=Entity" Name="FLR\_[srv04]@2025-10-19 05:59:18" />     </Links>   </Ref>   <Ref Type="RestoreSessionReference" Href="https://localhost:9398/api/restoreSessions/9e289dec-4c1d-4a76-bae0-2191104cb59d" Name="FLR\_[srv04]@2025-10-19 05:57:10" UID="urn:veeam:RestoreSession:9e289dec-4c1d-4a76-bae0-2191104cb59d">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="RestoreSession" Href="https://localhost:9398/api/restoreSessions/9e289dec-4c1d-4a76-bae0-2191104cb59d?format=Entity" Name="FLR\_[srv04]@2025-10-19 05:57:10" />     </Links>   </Ref>   <Ref Type="RestoreSessionReference" Href="https://localhost:9398/api/restoreSessions/6114f06d-143a-45be-9b07-371704f71092" Name="FLR\_[srv04]@2025-10-18 15:16:59" UID="urn:veeam:RestoreSession:6114f06d-143a-45be-9b07-371704f71092">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="RestoreSession" Href="https://localhost:9398/api/restoreSessions/6114f06d-143a-45be-9b07-371704f71092?format=Entity" Name="FLR\_[srv04]@2025-10-18 15:16:59" />     </Links>   </Ref>   <Ref Type="RestoreSessionReference" Href="https://localhost:9398/api/restoreSessions/c8fdd529-d4af-48b2-8ea0-5d8b91359929" Name="FLR\_[srv04]@2025-10-19 06:00:25" UID="urn:veeam:RestoreSession:c8fdd529-d4af-48b2-8ea0-5d8b91359929">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="RestoreSession" Href="https://localhost:9398/api/restoreSessions/c8fdd529-d4af-48b2-8ea0-5d8b91359929?format=Entity" Name="FLR\_[srv04]@2025-10-19 06:00:25" />     </Links>   </Ref>   <Ref Type="RestoreSessionReference" Href="https://localhost:9398/api/restoreSessions/e8cd647d-9f67-4919-ac7f-5fc014444458" Name="FLR\_[srv04]@2025-10-19 07:19:53" UID="urn:veeam:RestoreSession:e8cd647d-9f67-4919-ac7f-5fc014444458">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="RestoreSession" Href="https://localhost:9398/api/restoreSessions/e8cd647d-9f67-4919-ac7f-5fc014444458?format=Entity" Name="FLR\_[srv04]@2025-10-19 07:19:53" />     </Links>   </Ref>  </EntityReferences> |

Page updated 2026-07-28

