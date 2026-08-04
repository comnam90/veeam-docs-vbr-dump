---
title: "GET /replicaTaskSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_replicatasksessions.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /replicaTaskSessions


Returns a resource representation of a replication tasks collection. Tasks are performed on all backup servers connected to Veeam Backup Enterprise Manager. Note, the request only returns the sessions that has been created for the last 30 days.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of replication tasks, send the [GET /query?type=ReplicaJobSession](get_query_replicajobsession.md) request. |

Request

To get a list of replication tasks, send the GET HTTP request to the /replicaTaskSessions resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/replicaTaskSessions |

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

In the response body, the REST API returns a representation of the /replicaTaskSessions resource collection.

Example

The example below returns a list of all replication tasks performed on backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/replicaTaskSessions  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="ReplicaTaskSessionReference" Href="https://localhost:9398/api/repicaTaskSessions/1f2b40a8-2370-4280-a3f9-5f7c611d3f79" Name="sql02@2025-10-19 05:42:46" UID="urn:veeam:ReplicaTaskSession:1f2b40a8-2370-4280-a3f9-5f7c611d3f79">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="ReplicaJobSessionReference" Href="https://localhost:9398/api/replicaSessions/b04c217b-0538-4650-bec4-19deff4ea1ac" Name="SQL Replication" />       <Link Rel="Alternate" Type="ReplicaTaskSession" Href="https://localhost:9398/api/repicaTaskSessions/1f2b40a8-2370-4280-a3f9-5f7c611d3f79?format=Entity" Name="sql02@2025-10-19 05:42:46" />     </Links>   </Ref>   <Ref Type="ReplicaTaskSessionReference" Href="https://localhost:9398/api/repicaTaskSessions/24590151-20cd-4e57-8a2f-8b65869a1879" Name="srv04@2025-10-19 06:47:21" UID="urn:veeam:ReplicaTaskSession:24590151-20cd-4e57-8a2f-8b65869a1879">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="ReplicaJobSessionReference" Href="https://localhost:9398/api/replicaSessions/2c49a44e-1e59-4527-a6bc-6b2f9b579ee1" Name="Fileserver02 Replication" />       <Link Rel="Alternate" Type="ReplicaTaskSession" Href="https://localhost:9398/api/repicaTaskSessions/24590151-20cd-4e57-8a2f-8b65869a1879?format=Entity" Name="srv04@2025-10-19 06:47:21" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-28

