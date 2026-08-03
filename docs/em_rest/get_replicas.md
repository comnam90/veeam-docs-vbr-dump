---
title: "GET /replicas"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_replicas.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /replicas


Returns a resource representation of a collection of replicas created on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of replicas, send the [GET /query?type=Replica](get_query_replica.md) request. |

Request

To get a list of replicas, send the GET HTTP request to the /replicas resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/replicas |

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

In the response body, the REST API returns a representation of the /replicas resource collection.

Example

The example below returns a list of all replicas created on backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/replicas  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="ReplicaReference" Href="https://localhost:9398/api/replicas/6a725c36-7426-42df-a887-1ed7b88411d9" Name="replica 1" UID="urn:veeam:Replica:6a725c36-7426-42df-a887-1ed7b88411d9">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="RepositoryReference" Href="https://localhost:9398/api/repositories/bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6" Name="Backup Volume 01" />       <Link Rel="Alternate" Type="Replica" Href="https://localhost:9398/api/replicas/6a725c36-7426-42df-a887-1ed7b88411d9?format=Entity" Name="Oracle Replica" />       <Link Rel="Down" Type="VmReplicaPointReferenceList" Href="https://localhost:9398/api/replicas/6a725c36-7426-42df-a887-1ed7b88411d9/vmReplicaPoints" />     </Links>   </Ref>   <Ref Type="ReplicaReference" Href="https://localhost:9398/api/replicas/fe4d9334-8801-440c-9994-5a16181d7fb0" Name="SQL Replication" UID="urn:veeam:Replica:fe4d9334-8801-440c-9994-5a16181d7fb0">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="RepositoryReference" Href="https://localhost:9398/api/repositories/cbd9a4b6-b9ed-4cd6-a091-75b6481c9d55" Name="Default Backup Repository" />       <Link Rel="Alternate" Type="Replica" Href="https://localhost:9398/api/replicas/fe4d9334-8801-440c-9994-5a16181d7fb0?format=Entity" Name="AD Replication" />       <Link Rel="Down" Type="VmReplicaPointReferenceList" Href="https://localhost:9398/api/replicas/fe4d9334-8801-440c-9994-5a16181d7fb0/vmReplicaPoints" />     </Links>   </Ref>   <Ref Type="ReplicaReference" Href="https://localhost:9398/api/replicas/b745edde-cbde-4a74-b7a7-6d2f461c9287" Name="SQL Server Replication" UID="urn:veeam:Replica:b745edde-cbde-4a74-b7a7-6d2f461c9287">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Up" Type="RepositoryReference" Href="https://localhost:9398/api/repositories/cbd9a4b6-b9ed-4cd6-a091-75b6481c9d55" Name="Default Backup Repository" />       <Link Rel="Alternate" Type="Replica" Href="https://localhost:9398/api/replicas/b745edde-cbde-4a74-b7a7-6d2f461c9287?format=Entity" Name="SQL Server Replication" />       <Link Rel="Down" Type="VmReplicaPointReferenceList" Href="https://localhost:9398/api/replicas/b745edde-cbde-4a74-b7a7-6d2f461c9287/vmReplicaPoints" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

