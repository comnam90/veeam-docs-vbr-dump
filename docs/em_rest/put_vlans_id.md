---
title: "PUT /cloud/vlans/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/put_vlans_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Edits VLAN ranges that are reserved for Veeam Cloud Connect Replication on the virtual switch with the specified ID.

Request

To edit VLANs, send the PUT HTTP request to the /cloud/vlans/{ID} resource.

HTTP Request

|  |
| --- |
| PUT https://<Enterprise-Manager>:9398/api/cloud/vlans/{ID} |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters for the VLAN configuration resource that must be updated. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| HostRef | HierarchyObjRefType | Reference to the host on which the virtual switch with VLAN ranges is configured, for example: urn:VMware:Host:4a3f28d9-d4f3-4e4c-9afb-91db8ab57436.host-438. You can [construct the reference manually](constructing_hierarchyobjreftype.md) or use the [lookup service](lookupsvc.md) to retrieve the reference. | No | 0/1 |
| PlatformType | String | Platform of the virtualization host on which the virtual switch is configured. Possible values:   * VMware * HyperV | No | 0/1 |
| VlanIdsWithInternetLeftBound | Int | The first VLAN ID in the range of VLANs that will be used for providing networks with internet access to tenant VM replicas. | Yes | 0/1 |
| VlanIdsWithInternetRightBound | Int | The last VLAN ID in the range of VLANs that will be used for providing networks with internet access to tenant VM replicas. | Yes | 0/1 |
| VlanIdsWithoutInternetLeftBound | Int | The first VLAN ID in the range of VLANs that will be used for providing networks without internet access to tenant VM replicas. | Yes | 0/1 |
| VlanIdsWithoutInternetRightBound | Int | The last VLAN ID in the range of VLANs that will be used for providing networks without internet access to tenant VM replicas. | Yes | 0/1 |
| SwitchName | String | Name of the virtual switch on which VLAN ranges are configured, for example: vSwitch0. | No | 0/1 |
| SwitchId | String | ID of the virtual switch on which VLAN ranges are configured, for example: vSwitch0. | No | 0/1 |
| SwitchType | String | Type of the virtual switch on which VLAN ranges are configured. Possible values:   * VirtualSwitch * DistributedVirtualSwitch | No | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "HostRef": "urn:VMware:Host:4a3f28d9-d4f3-4e4c-9afb-91db8ab57436.host-438",   "PlatformType": "VMware",   "VlanIdsWithInternetLeftBound": 500,   "VlanIdsWithInternetRightBound": 510,   "VlanIdsWithoutInternetLeftBound": 511,   "VlanIdsWithoutInternetRightBound": 520,   "SwitchName": "vSwitch0",   "SwitchId": "vSwitch0",   "SwitchType": "VirtualSwitch",   "Name": "vSwitch0",   "UID": "78c6a038-38a2-4908-ac19-1540f9448533",  } |

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 202 Accepted.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

None.

Example

The example below updates ranges of VLANs with and without internet access on the virtual switch that has ID 78c6a038-38a2-4908-ac19-1540f9448533.

|  |
| --- |
| Request:  PUT https://localhost:9398/api/cloud/vlans/78c6a038-38a2-4908-ac19-1540f9448533    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <VlanConfiguration Name="vSwitch0" UID="78c6a038-38a2-4908-ac19-1540f9448533" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <HostRef>urn:VMware:Host:4a3f28d9-d4f3-4e4c-9afb-91db8ab57436.host-438</HostRef>   <PlatformType>VMware</PlatformType>   <VlanIdsWithInternetLeftBound>490</VlanIdsWithInternetLeftBound>   <VlanIdsWithInternetRightBound>510</VlanIdsWithInternetRightBound>   <VlanIdsWithoutInternetLeftBound>511</VlanIdsWithoutInternetLeftBound>   <VlanIdsWithoutInternetRightBound>530</VlanIdsWithoutInternetRightBound>   <SwitchName>vSwitch0</SwitchName>   <SwitchId>vSwitch0</SwitchId>   <SwitchType>VirtualSwitch</SwitchType> </VlanConfiguration>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>UpdateVlanConfiguration</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>UpdateVlanConfiguration</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
