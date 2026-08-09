---
title: "GET /cloud/replicas"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cloudreplicas.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cloud/replicas


Returns a resource representation of a collection of replicas created by tenants whose accounts are created on all backup servers connected to Veeam Backup Enterprise Manager.

The collection includes the following replica types:

* Regular replicas for VMware vSphere, Microsoft Hyper-V and VMware Cloud Director
* CDP replicas
* VMware Cloud Director CDP replicas

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of replicas created by tenants, send the [GET /query?type=CloudReplica](get_query_cloudreplica.md) request. |

Request

To get a list of replicas, send the GET HTTP request to the /cloud/replicas resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/replicas |

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

In the response body, the REST API returns a representation of the /cloud/replicas resource collection.

Example

The example below returns a list of replicas created by all tenants whose accounts are created on SP backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/replicas  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/8393c284-c953-403f-a9b9-cff63e0c6815" Name="ABC Company Servers Replication" UID="urn:veeam:CloudReplica:8393c284-c953-403f-a9b9-cff63e0c6815">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudReplica" Href="https://localhost:9398/api/cloud/replicas/8393c284-c953-403f-a9b9-cff63e0c6815?format=Entity" Name="ABC Company Servers Replication" />       <Link Rel="Down" Type="CloudVmReplicaPointReferenceList" Href="https://localhost:9398/api/cloud/vmReplicaPoints/8393c284-c953-403f-a9b9-cff63e0c6815/vmReplicaPoints" />     </Links>   </Ref>   <Ref Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/6b2b42d5-3850-421c-93c1-e063f12a2ead" Name="UCM Company CRM Replication" UID="urn:veeam:CloudReplica:6b2b42d5-3850-421c-93c1-e063f12a2ead">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudReplica" Href="https://localhost:9398/api/cloud/replicas/6b2b42d5-3850-421c-93c1-e063f12a2ead?format=Entity" Name="UCM Company CRM Replication" />       <Link Rel="Down" Type="CloudVmReplicaPointReferenceList" Href="https://localhost:9398/api/cloud/vmReplicaPoints/6b2b42d5-3850-421c-93c1-e063f12a2ead/vmReplicaPoints" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

