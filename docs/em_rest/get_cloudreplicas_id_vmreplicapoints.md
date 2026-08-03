---
title: "GET /cloud/replicas/{ID}/vmReplicaPoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cloudreplicas_id_vmreplicapoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cloud/replicas/{ID}/vmReplicaPoints


Returns a resource representation of a collection of restore points for separate VMs in a cloud replica with the specified ID.

The collection includes restore points of the following replica types:

* Regular replicas for VMware vSphere, Microsoft Hyper-V and VMware Cloud Director
* CDP replicas
* VMware Cloud Director CDP replicas

Request

To get a list of restore points for separate tenant VMs in a cloud replica with the specified ID, send the GET HTTP request to the /cloud/replicas/{ID}/vmReplicaPoints resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/replicas/{ID}/vmReplicaPoints |

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

In the response body, the REST API returns a representation of the /cloud/replicas/{ID}/vmReplicaPoints resource collection.

Example

A sample request below returns a list of all VM replica restore points in a replica with ID 8393c284-c953-403f-a9b9-cff63e0c6815.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/replicas/8393c284-c953-403f-a9b9-cff63e0c6815/vmReplicaPoints  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CloudVmReplicaPointReference" Href="https://localhost:9398/api/cloud/vmReplicaPoints/908d5660-9658-4689-a11b-0c188bc4cc4d" Name="srv38@2025-01-04 21:03:57" UID="urn:veeam:CloudVmReplicaPoint:908d5660-9658-4689-a11b-0c188bc4cc4d">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Up" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/8393c284-c953-403f-a9b9-cff63e0c6815" Name="ABC Company Servers Replication" />       <Link Rel="Alternate" Type="CloudVmReplicaPoint" Href="https://localhost:9398/api/cloud/vmReplicaPoints/908d5660-9658-4689-a11b-0c188bc4cc4d?format=Entity" Name="srv38@2025-01-04 21:03:57" />     </Links>   </Ref>   <Ref Type="CloudVmReplicaPointReference" Href="https://localhost:9398/api/cloud/vmReplicaPoints/33785d35-5e73-4ec0-b2c7-1ff7a6dfd979" Name="srv40@2025-01-10 21:08:16" UID="urn:veeam:CloudVmReplicaPoint:33785d35-5e73-4ec0-b2c7-1ff7a6dfd979">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Up" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/8393c284-c953-403f-a9b9-cff63e0c6815" Name="ABC Company Servers Replication" />       <Link Rel="Alternate" Type="CloudVmReplicaPoint" Href="https://localhost:9398/api/cloud/vmReplicaPoints/33785d35-5e73-4ec0-b2c7-1ff7a6dfd979?format=Entity" Name="srv40@2025-01-10 21:08:16" />     </Links>   </Ref>   <Ref Type="CloudVmReplicaPointReference" Href="https://localhost:9398/api/cloud/vmReplicaPoints/3cda6d11-afa1-4842-b718-2747cfc845f2" Name="srv38@2025-01-05 21:03:42" UID="urn:veeam:CloudVmReplicaPoint:3cda6d11-afa1-4842-b718-2747cfc845f2">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Up" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/8393c284-c953-403f-a9b9-cff63e0c6815" Name="ABC Company Servers Replication" />       <Link Rel="Alternate" Type="CloudVmReplicaPoint" Href="https://localhost:9398/api/cloud/vmReplicaPoints/3cda6d11-afa1-4842-b718-2747cfc845f2?format=Entity" Name="srv38@2025-01-05 21:03:42" />     </Links>   </Ref>   <Ref Type="CloudVmReplicaPointReference" Href="https://localhost:9398/api/cloud/vmReplicaPoints/90fc78c0-2d6c-48f7-b01b-4d0cd30977e1" Name="srv40@2025-01-08 21:08:06" UID="urn:veeam:CloudVmReplicaPoint:90fc78c0-2d6c-48f7-b01b-4d0cd30977e1">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Up" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/8393c284-c953-403f-a9b9-cff63e0c6815" Name="ABC Company Servers Replication" />       <Link Rel="Alternate" Type="CloudVmReplicaPoint" Href="https://localhost:9398/api/cloud/vmReplicaPoints/90fc78c0-2d6c-48f7-b01b-4d0cd30977e1?format=Entity" Name="srv40@2025-01-08 21:08:06" />     </Links>   </Ref>   <Ref Type="CloudVmReplicaPointReference" Href="https://localhost:9398/api/cloud/vmReplicaPoints/085a71f7-7582-4f0c-84d4-52ab2d9ceab9" Name="srv38@2025-01-06 21:03:55" UID="urn:veeam:CloudVmReplicaPoint:085a71f7-7582-4f0c-84d4-52ab2d9ceab9">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Up" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/8393c284-c953-403f-a9b9-cff63e0c6815" Name="ABC Company Servers Replication" />       <Link Rel="Alternate" Type="CloudVmReplicaPoint" Href="https://localhost:9398/api/cloud/vmReplicaPoints/085a71f7-7582-4f0c-84d4-52ab2d9ceab9?format=Entity" Name="srv38@2025-01-06 21:03:55" />     </Links>   </Ref>   ... </EntityReferences> |

Page updated 2026-07-29

