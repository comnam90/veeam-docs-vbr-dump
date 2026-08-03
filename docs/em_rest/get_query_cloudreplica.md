---
title: "GET /query?type=CloudReplica"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_cloudreplica.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=CloudReplica


Returns a resource representation of a collection of replicas created by tenants whose accounts are created on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/cloud/replicas](cloudreplicas.md).

The collection includes the following replica types:

* Regular replicas for VMware vSphere, Microsoft Hyper-V and VMware Cloud Director
* CDP replicas
* VMware Cloud Director CDP replicas

Request

To get a list of replicas, send the GET HTTP request to the query with the type parameter set to CloudReplica.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=CloudReplica |

Request Headers

The request contains the following headers:

Request Headers

| Header | Required | Description |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Optional Parameters

In the query, you can use the following parameters for filtering and sorting.

Optional Parameters

| Parameter | Type | Description |
| UID | UidType | UID of the cloud replica resource, for example: urn:veeam:CloudReplica:8393c284-c953-403f-a9b9-cff63e0c6815. |
| Name | String | Name of the cloud replica resource, for example: ABC Company Servers Replication. |
| Platform | String | Platform for which the replication job parent to the replica is created. Possible values:   * VMware * HyperV * vCloud |

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

In the response body, the REST API returns a representation of the /cloud/replicas resource collection.

Example

The example below returns an entity resource representation of a collection of replicas created by tenants for VMware vSphere objects. The results are ordered in the acceding order by the Name parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=CloudReplica&format=Entities&sortAsc=Name&filter=Platform==VMware  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <CloudReplicas>       <CloudReplica Type="CloudReplica" Href="https://localhost:9398/api/cloud/replicas/8e7b8830-e42a-4b3e-b4fe-b52f1fccc91a?format=Entity" Name="Servers Replication" UID="urn:veeam:CloudReplica:8e7b8830-e42a-4b3e-b4fe-b52f1fccc91a">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ca19249e-e638-421a-ab22-68cb89b9009a" Name="172.24.31.67" />           <Link Rel="Alternate" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/8e7b8830-e42a-4b3e-b4fe-b52f1fccc91a" Name="Servers Replication" />           <Link Rel="Down" Type="CloudVmReplicaPointReferenceList" Href="https://localhost:9398/api/cloud/replicas/8e7b8830-e42a-4b3e-b4fe-b52f1fccc91a/vmReplicaPoints" />         </Links>         <Platform>VMware</Platform>       </CloudReplica>       <CloudReplica Type="CloudReplica" Href="https://localhost:9398/api/cloud/replicas/ddb68d1e-9035-4e78-9797-eae356e715f9?format=Entity" Name="Webserver Replication" UID="urn:veeam:CloudReplica:ddb68d1e-9035-4e78-9797-eae356e715f9">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ca19249e-e638-421a-ab22-68cb89b9009a" Name="172.24.31.67" />           <Link Rel="Alternate" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/ddb68d1e-9035-4e78-9797-eae356e715f9" Name="Webserver Replication" />           <Link Rel="Down" Type="CloudVmReplicaPointReferenceList" Href="https://localhost:9398/api/cloud/replicas/ddb68d1e-9035-4e78-9797-eae356e715f9/vmReplicaPoints" />         </Links>         <Platform>VMware</Platform>       </CloudReplica>       <CloudReplica Type="CloudReplica" Href="https://localhost:9398/api/cloud/replicas/042fc8d4-0f23-459c-9e5a-82614b3121cc?format=Entity" Name="Webserver Replication" UID="urn:veeam:CloudReplica:042fc8d4-0f23-459c-9e5a-82614b3121cc">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ca19249e-e638-421a-ab22-68cb89b9009a" Name="172.24.31.67" />           <Link Rel="Alternate" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/042fc8d4-0f23-459c-9e5a-82614b3121cc" Name="Webserver Replication" />           <Link Rel="Down" Type="CloudVmReplicaPointReferenceList" Href="https://localhost:9398/api/cloud/replicas/042fc8d4-0f23-459c-9e5a-82614b3121cc/vmReplicaPoints" />         </Links>         <Platform>VMware</Platform>       </CloudReplica>       <CloudReplica Type="CloudReplica" Href="https://localhost:9398/api/cloud/replicas/26938b05-87ca-4bc7-a815-ae87e76cca89?format=Entity" Name="Webserver Replication" UID="urn:veeam:CloudReplica:26938b05-87ca-4bc7-a815-ae87e76cca89">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ca19249e-e638-421a-ab22-68cb89b9009a" Name="172.24.31.67" />           <Link Rel="Alternate" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/26938b05-87ca-4bc7-a815-ae87e76cca89" Name="Webserver Replication" />           <Link Rel="Down" Type="CloudVmReplicaPointReferenceList" Href="https://localhost:9398/api/cloud/replicas/26938b05-87ca-4bc7-a815-ae87e76cca89/vmReplicaPoints" />         </Links>         <Platform>VMware</Platform>       </CloudReplica>     </CloudReplicas>   </Entities>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=CloudReplica&format=Entities&sortAsc=Name&filter=Platform==VMware&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=CloudReplica&format=Entities&sortAsc=Name&filter=Platform==VMware&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

