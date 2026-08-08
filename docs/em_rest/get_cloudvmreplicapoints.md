---
title: "GET /cloud/vmReplicaPoints"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cloudvmreplicapoints.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cloud/vmReplicaPoints


Returns a resource representation of a collection of restore points for separate VMs that are replicated with tenant replication jobs.

The collection includes restore points of the following replica types:

* Regular replicas for VMware vSphere, Microsoft Hyper-V and VMware Cloud Director
* CDP replicas
* VMware Cloud Director CDP replicas

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of restore points for separate replicated VMs, send the [GET /query?type=CloudVmReplicaPoint](get_query_cloudvmreplicapoint.md) request. |

HTTP Request

To get a list of restore points, send the GET HTTP request to the /cloud/vmReplicaPoints resource.

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/vmReplicaPoints |

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

In the response body, the REST API returns a representation of the /cloud/vmReplicaPoints resource collection.

Example

The example below returns a list of all VM replica restore points created by tenants whose accounts had been created on backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/vmReplicaPoints  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CloudVmReplicaPointReference" Href="https://localhost:9398/api/cloud/vmReplicaPoints/93081441-6e3c-4584-b47a-08dc1ce24f84" Name="srv39@2025-12-25 20:00:47" UID="urn:veeam:CloudVmReplicaPoint:93081441-6e3c-4584-b47a-08dc1ce24f84">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Up" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/6b2b42d5-3850-421c-93c1-e063f12a2ead" Name="UCM Company CRM Replication" />       <Link Rel="Alternate" Type="CloudVmReplicaPoint" Href="https://localhost:9398/api/cloud/vmReplicaPoints/93081441-6e3c-4584-b47a-08dc1ce24f84?format=Entity" Name="srv39@2025-12-25 20:00:47" />     </Links>   </Ref>   <Ref Type="CloudVmReplicaPointReference" Href="https://localhost:9398/api/cloud/vmReplicaPoints/783781f0-4d83-4d09-ae82-12b5bed4710b" Name="srv40@2025-12-27 21:08:13" UID="urn:veeam:CloudVmReplicaPoint:783781f0-4d83-4d09-ae82-12b5bed4710b">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Up" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/8393c284-c953-403f-a9b9-cff63e0c6815" Name="ABC Company Servers Replication" />       <Link Rel="Alternate" Type="CloudVmReplicaPoint" Href="https://localhost:9398/api/cloud/vmReplicaPoints/783781f0-4d83-4d09-ae82-12b5bed4710b?format=Entity" Name="srv40@2025-12-27 21:08:13" />     </Links>   </Ref>   <Ref Type="CloudVmReplicaPointReference" Href="https://localhost:9398/api/cloud/vmReplicaPoints/292e6d96-6b99-4776-bba2-2c030cd5824a" Name="srv38@2025-12-21 21:01:41" UID="urn:veeam:CloudVmReplicaPoint:292e6d96-6b99-4776-bba2-2c030cd5824a">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Up" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/8393c284-c953-403f-a9b9-cff63e0c6815" Name="ABC Company Servers Replication" />       <Link Rel="Alternate" Type="CloudVmReplicaPoint" Href="https://localhost:9398/api/cloud/vmReplicaPoints/292e6d96-6b99-4776-bba2-2c030cd5824a?format=Entity" Name="srv38@2025-12-21 21:01:41" />     </Links>   </Ref>   <Ref Type="CloudVmReplicaPointReference" Href="https://localhost:9398/api/cloud/vmReplicaPoints/5ed13778-0191-4d9d-8105-33017348235d" Name="srv40@2025-12-22 21:05:43" UID="urn:veeam:CloudVmReplicaPoint:5ed13778-0191-4d9d-8105-33017348235d">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Up" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/8393c284-c953-403f-a9b9-cff63e0c6815" Name="ABC Company Servers Replication" />       <Link Rel="Alternate" Type="CloudVmReplicaPoint" Href="https://localhost:9398/api/cloud/vmReplicaPoints/5ed13778-0191-4d9d-8105-33017348235d?format=Entity" Name="srv40@2025-12-22 21:05:43" />     </Links>   </Ref>   <Ref Type="CloudVmReplicaPointReference" Href="https://localhost:9398/api/cloud/vmReplicaPoints/574c07de-50eb-4117-88ec-5cd3403142dd" Name="srv38@2025-12-24 21:03:50" UID="urn:veeam:CloudVmReplicaPoint:574c07de-50eb-4117-88ec-5cd3403142dd">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Up" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/8393c284-c953-403f-a9b9-cff63e0c6815" Name="ABC Company Servers Replication" />       <Link Rel="Alternate" Type="CloudVmReplicaPoint" Href="https://localhost:9398/api/cloud/vmReplicaPoints/574c07de-50eb-4117-88ec-5cd3403142dd?format=Entity" Name="srv38@2025-12-24 21:03:50" />     </Links>   </Ref>   <Ref Type="CloudVmReplicaPointReference" Href="https://localhost:9398/api/cloud/vmReplicaPoints/572167d1-c2f1-40b5-9ce9-6b277e507222" Name="srv39@2025-12-22 11:25:26" UID="urn:veeam:CloudVmReplicaPoint:572167d1-c2f1-40b5-9ce9-6b277e507222">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Up" Type="CloudReplicaReference" Href="https://localhost:9398/api/cloud/replicas/6b2b42d5-3850-421c-93c1-e063f12a2ead" Name="UCM Company CRM Replication" />       <Link Rel="Alternate" Type="CloudVmReplicaPoint" Href="https://localhost:9398/api/cloud/vmReplicaPoints/572167d1-c2f1-40b5-9ce9-6b277e507222?format=Entity" Name="srv39@2025-12-22 11:25:26" />     </Links>   </Ref>   ... </EntityReferences> |

Page updated 2026-07-29

