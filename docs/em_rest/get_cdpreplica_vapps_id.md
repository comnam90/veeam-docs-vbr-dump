---
title: "get_cdpreplica_vapps_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cdpreplica_vapps_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a vApp having the specified ID and replicated by a CDP policy for VMware Cloud Director.

Request

To get a vApp having the specified ID, send the GET HTTP request to the /cdpReplica/vApp/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cdpReplica/vApps/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /cdpReplica/vApps/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the vApp included in the CDP replica, for example: urn:veeam:VAppCdpReplica:571252ff-c227-4204-b9f8-e1f32a52496b. |
| Name | String | Name of the vApp included in the CDP replica, for example: vApp-TS. |
| vAppRef | HierarchyObjRefType | Reference to the vApp, for example: urn:vCloud:Vapp:1903878c-230d-456d-80d2-4df9e319b6d7.urn:vcloud:vapp:aff5d61d-4481-4f72-a019-e0ed1bbd63a3. |
| ReplicaUid | UidType | ID of the CDP replica, for example: fdab78b8-8cee-4939-b478-276dbcd25de4. |
| BackupServer | String | Name of the backup server parent to the CDP replica resource. |
| PolicyUid | UidType | ID of the CDP policy that processes the vApp, for example: 872a3860-3805-43b8-bcf6-388384bfed33. |
| PolicyName | String | Name of the CDP policy that processes the vApp. |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the CDP policy was configured. |
| /cdpReplicas/vApps/{ID} | Alternate | Alternate URL of the [/cdpReplica/vApps/{ID}](cdpreplica_vapps_id.md) resource. |
| /cdpReplicas/vApps/{ID}/vms | Down | URL of the [/cdpReplica/vApps/{ID}/vms](cdpreplica_vapps_id_vms.md) resource — a collection of VMs contained in the vApp. |
| /cdpReplica/vApps/{ID}?action=intervals | Intervals | URL for the [POST /cdpReplica/vApps/{ID}?action=intervals](post_cdpreplicavapp_id_actionintervals.md) request. |
| /cdpReplicas/vApps/{ID}?action=failover | Failover | URL for the [POST /cdpReplica/vApps/{ID}?action=failover](post_cdpreplicavapp_id_actionfailover.md) request. |
| /cdpPolicies/{ID} | Up | URL of the [/cdpPolicies/{ID}](cdppolicies_id.md) resource — a CDP policy that processes the replica. |

Example

The example below returns an entity resource representation of the vApp having ID 4d408966-827f-4142-811f-90be94c842a9.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <VAppCdpReplica xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0" Href="https://enterprise04.tech.local:9398/api/cdpReplica/vApps/4d408966-827f-4142-811f-90be94c842a9?format=Entity" Type="VAppCdpReplica" Name="vApp02" UID="urn:veeam:VAppCdpReplica:4d408966-827f-4142-811f-90be94c842a9"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
