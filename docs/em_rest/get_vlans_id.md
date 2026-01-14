---
title: "get_vlans_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_vlans_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a virtual switch with the specified ID on which VLAN ranges for Veeam Cloud Connect Replication are reserved. VLANs are used for providing networking capabilities to tenant VM replicas. The virtual switch is configured on the virtualization host that is used as a replication target and connected to the backup server managed by Veeam Backup Enterprise Manager.

Request

To get a virtual switch with the specified ID on which VLAN ranges are configured, send the GET HTTP request to the /cloud/vlans/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/vlans/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /cloud/vlans/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | String | ID of the virtual switch in the Veeam infrastructure, for example: 510f34ea-1534-437c-a746-f32cf0f712aa. |
| Name | String | Name of the virtual switch, for example: Intel(R) I350 Gigabit Network Connection - Virtual Switch. |
| HostRef | HierarchyObjRefType | Reference to the host on which the virtual switch is configured, for example: urn:VMware:Host:4a3f28d9-d4f3-4e4c-9afb-91db8ab57436.host-438. |
| PlatformType | String | Platform of the virtualization host on which the virtual switch is configured. Possible values:   * VMware * HyperV |
| VlanIdsWithInternetLeftBound | Int | The first VLAN ID in the range of VLANs that are used for providing networks with internet access to tenant VM replicas. |
| VlanIdsWithInternetRightBound | Int | The last VLAN ID in the range of VLANs that are used for providing networks with internet access to tenant VM replicas. |
| VlanIdsWithoutInternetLeftBound | Int | The first VLAN ID in the range of VLANs that are used for providing networks without internet access to tenant VM replicas. |
| VlanIdsWithoutInternetRightBound | Int | The last VLAN ID in the range of VLANs that are used for providing networks without internet access to tenant VM replicas. |
| SwitchName | String | Name of the virtual switch, for example: Intel(R) I350 Gigabit Network Connection - Virtual Switch. |
| SwitchId | String | ID of the virtual switch in the virtualization infrastructure, for example: 4670EE6D-66BE-4A1C-A58E-6389CA99BD3E. |
| ClusterName | String | Name of the cluster on which the virtual switch with VLAN ranges is configured. |
| ClusterId | String | ID of the cluster on which the virtual switch with VLAN ranges is configured. |
| SwitchType | String | Type of the virtual switch. Possible values:   * VirtualSwitch * DistributedVirtualSwitch |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=VlanConfiguration](get_query_vlanconfiguration.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the VLAN was configured. |
| /cloud/vlans/{ID} | Alternate | Alternate URL of the [/cloud/vlans/{ID}](vlans_id.md) resource. |
| /cloud/vlans/{ID} | Edit | URL for the [PUT /cloud/vlans/{ID}](put_vlans_id.md) request. |
| /cloud/vlans/{ID} | Delete | URL for the [DELETE /cloud/vlans/{ID}](delete_vlans_id.md) request. |

Example

The example below returns a virtual switch with the ID 78c6a038-38a2-4908-ac19-1540f9448533 on which VLAN ranges are configured.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/vlans/78c6a038-38a2-4908-ac19-1540f9448533?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <VlanConfiguration xmlns="http://www.veeam.com/ent/v1.0" Name="vSwitch0" UID="78c6a038-38a2-4908-ac19-1540f9448533"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
