---
title: "GET /cdpReplica/vApps/{ID}/vms"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cdpreplica_vapps_id_vms.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cdpReplica/vApps/{ID}/vms


Returns a resource representation of a collection of VMs contained in a vApp having the specified ID

Request

To get a collection of VMs contained in a vApp having the specified ID, send the GET HTTP request to the /cdpReplica/vApps/{ID}/vms resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cdpReplica/vApps/{ID}/vms |

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

In the response body, the REST API returns an entity or an entity reference of the/cdpReplica/vApps/{ID}/vms resource collection.

Example

The example below returns an entity resource representation of a collection of VMs contained in the the vApp having ID 4d408966-827f-4142-811f-90be94c842a9.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9/vms  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <VAppCdpReplicaVms xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">   <Items Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9/vms/6f6b3a9d-30a9-498c-bf3b-4ec1893f7e7a?format=Entity" Type="VAppCdpReplicaVm" Name="vm02-DlmR" UID="urn:veeam:VAppCdpReplicaVm:6f6b3a9d-30a9-498c-bf3b-4ec1893f7e7a">     <Links>       <Link Href="https://enterprise04.tech.local:9398/api/backupServers/e7b45d02-9017-4773-9398-ccb4f0f336df" Name="backupsrv52.tech.local" Type="BackupServerReference" Rel="Up"/>       <Link Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9/vms/6f6b3a9d-30a9-498c-bf3b-4ec1893f7e7a?format=Reference" Name="vm02-DlmR" Type="VAppCdpReplicaVmReference" Rel="Alternate"/>       <Link Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9" Name="vApp02" Type="VAppCdpReplicaReference" Rel="Up"/>       <Link Href="https://enterprise04.tech.local:9398/api/cdpPolicies/8846d24b-d12f-4b7a-94e2-8c78241b841e" Name="CDP Policy Cloud Director" Type="CdpPolicyReference" Rel="Up"/>     </Links>     <ReplicaUid>4d408966-827f-4142-811f-90be94c842a9</ReplicaUid>     <VmRef>urn:VMware:Vm:310bf182-930c-494e-ab0d-636c5eba58b9.vm-4220</VmRef>   </Items>   <Items Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9/vms/a5127596-0076-4cae-9144-ecec955b045a?format=Entity" Type="VAppCdpReplicaVm" Name="vApp02-kAd4" UID="urn:veeam:VAppCdpReplicaVm:a5127596-0076-4cae-9144-ecec955b045a">     <Links>       <Link Href="https://enterprise04.tech.local:9398/api/backupServers/e7b45d02-9017-4773-9398-ccb4f0f336df" Name="backupsrv52.tech.local" Type="BackupServerReference" Rel="Up"/>       <Link Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9/vms/a5127596-0076-4cae-9144-ecec955b045a?format=Reference" Name="vApp02-kAd4" Type="VAppCdpReplicaVmReference" Rel="Alternate"/>       <Link Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9" Name="vApp02" Type="VAppCdpReplicaReference" Rel="Up"/>       <Link Href="https://enterprise04.tech.local:9398/api/cdpPolicies/8846d24b-d12f-4b7a-94e2-8c78241b841e" Name="CDP Policy Cloud Director" Type="CdpPolicyReference" Rel="Up"/>     </Links>     <ReplicaUid>4d408966-827f-4142-811f-90be94c842a9</ReplicaUid>     <VmRef>urn:VMware:Vm:310bf182-930c-494e-ab0d-636c5eba58b9.vm-4216</VmRef>   </Items> </VAppCdpReplicaVms> |

Page updated 2026-07-29

