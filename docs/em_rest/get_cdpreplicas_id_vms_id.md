---
title: "GET /cdpReplicas/{ID}/vms/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cdpreplicas_id_vms_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a VM having the specified ID and included in the CDP replica with the specified ID.

Request

To get a VM  having the specified ID, send the GET HTTP request to the /cdpReplicas/{ID}/vms/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cdpReplicas/{ID}/vms/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /cdpReplicas/{ID}/vms/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the VM included in the CDP replica, for example: urn:veeam:CdpReplicaVm:6d9cb796-3c00-4fc5-bb99-3ad442e13eed. |
| Name | String | Name of the VM included in the CDP replica, for example: virt03-ubuntu01. |
| VmRef | HierarchyObjRefType | Reference to the VM, for example: urn:VMware:Vm:d68c782f-ec0a-4bf3-b3c1-04c552b64fdf.vm-85541. |
| ReplicaUid | UidType | ID of the CDP replica, for example: fdab78b8-8cee-4939-b478-276dbcd25de4. |
| BackupServer | String | Name of the backup server parent to the CDP replica resource. |
| PolicyUid | UidType | ID of the CDP policy that processes the VM, for example: 872a3860-3805-43b8-bcf6-388384bfed33. |
| PolicyName | String | Name of the CDP policy that processes the VM. |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /cdpReplicas/{ID}/vms/{ID}?action=intervals | Intervals | URL for the [POST /cdpReplicas/{ID}/vms/{ID}?action=intervals](post_cdpreplicavm_id_actionintervals.md) request. |
| /cdpReplicas/{ID}/vms/{ID}?action=failover | Failover | URL for the [POST /cdpReplicas/{ID}/vms/{ID}?action=failover](post_cdpreplicavm_id_actionfailover.md) request. |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the CDP policy was configured. |
| /cdpPolicies/{ID} | Up | URL of the [/cdpPolicies/{ID}](cdppolicies_id.md) resource — a CDP policy that processes the replica. |
| /cdpReplicas/{ID} | Up | URL of the [/cdpReplicas/{ID}](cdpreplicas_id.md) resource — a CDP replica that contains the VM. |

Example

The example below returns an entity resource representation of the VM having ID fc2d6425-e96d-44e7-9d96-b7af5991adb3 and included in the CDP replica with ID 24ae37ad-4d28-4568-8467-98d8770bb722.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cdpReplicas/24ae37ad-4d28-4568-8467-98d8770bb722/vms/fc2d6425-e96d-44e7-9d96-b7af5991adb3    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <?xml version="1.0" encoding="utf-8"?> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
