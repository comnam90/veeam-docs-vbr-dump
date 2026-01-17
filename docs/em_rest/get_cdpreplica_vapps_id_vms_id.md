---
title: "GET /cdpReplica/vApps/{ID}/vms/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cdpreplica_vapps_id_vms_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a VM with the specified ID that is contained in a vApp having the specified vApp ID.

Request

To get a VM with the specified ID that is contained in a vApp having the specified vApp ID, send the GET HTTP request to the /cdpReplica/vApps/{ID}/vms/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cdpReplica/vApps/{ID}/vms/{ID} |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
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

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns an entity or an entity reference of the/cdpReplica/vApps/{ID}/vms/{ID} resource collection. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the VM included in the CDP replica, for example: urn:veeam:VAppCdpReplicaVm:a5127596-0076-4cae-9144-ecec955b045a. |
| Name | String | Name of the VM included in the CDP replica, for example: virt03-ubuntu01. |
| ReplicaUid | UidType | ID of the CDP replica, for example: fdab78b8-8cee-4939-b478-276dbcd25de4. |
| VmRef | HierarchyObjRefType | Reference to the VM, for example: urn:VMware:Vm:310bf182-930c-494e-ab0d-636c5eba58b9.vm-4216. |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the CDP policy was configured. |
| /cdpReplicas/vApps/{ID}/vms/{ID} | Alternate | Alternate URL of the [/cdpReplica/vApps/{ID}/vms/{ID}](cdpreplica_vapps_id_vms_id.md) resource. |
| /cdpReplicas/vApps/{ID} | Up | URL of the [/cdpReplica/vApps/{ID}](cdpreplica_vapps_id.md) resource — a vApp that contains the VM. |
| /cdpPolicies/{ID} | Up | URL of the [/cdpPolicies/{ID}](cdppolicies_id.md) resource — a CDP policy that processes the VM. |

Example

The example below returns an entity resource representation of a VM with the a5127596-0076-4cae-9144-ecec955b045a ID that is contained in a vApp having ID 4d408966-827f-4142-811f-90be94c842a9.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9/vms/a5127596-0076-4cae-9144-ecec955b045a    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <VAppCdpReplicaVm xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0" Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9/vms/a5127596-0076-4cae-9144-ecec955b045a?format=Entity" Type="VAppCdpReplicaVm" Name="vApp02-kAd4" UID="urn:veeam:VAppCdpReplicaVm:a5127596-0076-4cae-9144-ecec955b045a"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
