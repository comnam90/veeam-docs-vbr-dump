---
title: "GET /vmReplicaPoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_vmreplicapoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /vmReplicaPoints


Returns a resource representation of a collection of restore points for separate replicated VMs.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of restore points for separate replicated VMs, send the [GET /query?type=ReplicaJobSession](get_query_replicajobsession.md) request. |

Request

To get a list of restore points for separate replicated VMs, send the GET HTTP request to the /vmReplicaPoints resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/vmReplicaPoints |

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

In the response body, the REST API returns a representation of the /vmReplicaPoints resource collection.

Example

The example below returns a list of all VM replica restore points created on backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/vmReplicaPoints  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="VmReplicaPointReference" Href="https://localhost:9398/api/vmReplicaPoints/d7c01ea7-89be-441d-8a9b-4a5d6a0183f5" Name="sql02@2025-10-07 13:05:59" UID="urn:veeam:VmReplicaPoint:d7c01ea7-89be-441d-8a9b-4a5d6a0183f5">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="ReplicaReference" Href="https://localhost:9398/api/replicas/fe4d9334-8801-440c-9994-5a16181d7fb0" Name="SQL Replication" />       <Link Rel="Alternate" Type="VmReplicaPoint" Href="https://localhost:9398/api/vmReplicaPoints/d7c01ea7-89be-441d-8a9b-4a5d6a0183f5?format=Entity" Name="sql02@2025-10-07 13:05:59" />     </Links>   </Ref>   <Ref Type="VmReplicaPointReference" Href="https://localhost:9398/api/vmReplicaPoints/9b414afe-e957-4d40-a144-7d02de9a041c" Name="sql02@2025-10-19 05:44:54" UID="urn:veeam:VmReplicaPoint:9b414afe-e957-4d40-a144-7d02de9a041c">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="ReplicaReference" Href="https://localhost:9398/api/replicas/fe4d9334-8801-440c-9994-5a16181d7fb0" Name="SQL Replication" />       <Link Rel="Alternate" Type="VmReplicaPoint" Href="https://localhost:9398/api/vmReplicaPoints/9b414afe-e957-4d40-a144-7d02de9a041c?format=Entity" Name="sql02@2025-10-19 05:44:54" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

