---
title: "POST /cloud/tenants/{ID}/vCloudComputeResources"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_cloud_tenants_id_vcloudcomputeresources.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# POST /cloud/tenants/{ID}/vCloudComputeResources


Assigns an organization VDC to a VMware Cloud Director tenant account with the specified ID.

Request

To assign an organization VDC to the VMware Cloud Director tenant account, send the POST HTTP request to the /cloud/tenants/{ID}/vCloudComputeResources resource.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}/vCloudComputeResources |

Request Header

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters of replication resources. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| VirtualDataCenterRef | HierarchyObjRefType | Reference to the organization VDC. The reference can be [constructed manually](constructing_hierarchyobjreftype.md) or obtained with the lookup service. For details on using the lookup, see [Virtual Infrastructure Lookup](lookup_service.md). | Yes | 1/1 |
| UseNetworkFailoverResources | Boolean | Defines whether the network extension appliance must be deployed for the VMware Cloud Director tenant account. Possible values:   * True * False | Yes | 1/1 |
| NetworkAppliance | NetworkApplianceInfoType | If UseNetworkFailoverResources option is set to True, you can pass parameters for the network extension appliance in the NetworkAppliance section of the request body. For details, see [Network Extension Options](#appliance). | Yes | 0/1 |
| WanAcceleratorUid | UidType | UID of the WAN accelerator that must be used as a target WAN accelerator. This parameter must be specified if you want tenants to communicate with cloud hosts through WAN accelerators. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "VirtualDataCenterRef": "urn:vCloud:OrgVdc:e923e20c-e114-4358-90d4-363d7de928f3.urn:vcloud:vdc:c20a16a7-2d09-4374-850d-84b1d6c9f7f3",   "UseNetworkFailoverResources": true,   "WanAcceleratorUid": "urn:veeam:WanAccelerator:b14583a5-d617-46e9-8edc-11617db73953"  } |

Network Extension Options

If you set the UseNetworkFailoverResources option to True, you can specify settings for the network extension appliance that will be deployed for the VMware Cloud Director tenant account in the SP infrastructure. The network extension appliance will act as a gateway between the SP production network and tenant VM replica networks providing resources for cloud VM replica failover.

You must define parameters for the network extension appliance in the NetworkAppliance section of the request body. The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Name | String | Name for the network extension appliance. | Yes | 1/1 |
| ProductionNetwork | String | Network label that identifies the port group to which you want to connect the network extension appliance. The port group is configured on the virtual switch in the SP virtualization environment and provides networking for the Veeam Cloud Connect infrastructure. | Yes | 1/1 |
| ObtainIpAddressAutomatically | Boolean | Defines whether network settings must be configured automatically for the network extension appliance. Possible values:   * True * False   If you set this option to False, you must pass network settings for the network extension appliance in the ManualIPAdressSettings section of the request body. For details, see [Manual Ip Addressing Options](#ip). | Yes | 1/1 |
| ViDistributedSwitchUuid | String | UID of the Distributed Virtual Switch on which the port group specified in the ProductionNetwork field is configured. | Yes | 0/1 |
| ProductionNetworkUnderDvs | Boolean | Defines whether the port group to which the network extension appliance must be connected is configured on a Distributed Virtual Switch. Possible values:   * True * False   If you set this option to True, you must pass ID of the Distributed Virtual Switch in the ViDistributedSwitch field. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <NetworkAppliance>   <Name>ApplianceDVS</Name>   <ProductionNetwork>pd-dvPortGroup-01</ProductionNetwork>   <ObtainIPAddressAutomatically>true</ObtainIPAddressAutomatically>   <ViDistributedSwitchUuid>4f 4b 14 50 21 97 3e 66-32 e7 95 50 f0 83 af b3</ViDistributedSwitchUuid>   <ProductionNetworkUnderDvs>true</ProductionNetworkUnderDvs> </NetworkAppliance> |

JSON Representation

|  |
| --- |
| "NetworkAppliance": {   "Name": "ApplianceDVS",   "ProductionNetwork": "pd-dvPortGroup-01",   "ObtainIPAddressAutomatically": "true",   "ViDistributedSwitchUuid": "4f 4b 14 50 21 97 3e 66-32 e7 95 50 f0 83 af b3",   "ProductionNetworkUnderDvs": "true"  } |

Manual IP Addressing Options

To assign the specific IP address to the network extension appliance, you must pass the following parameters in the ManualIpAddressSettingsInfoType section of the request body:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| IpAddress | IPv4 | IP address for the network extension appliance. | Yes | 1/1 |
| SubnetMask | IPv4 | Subnet mask for the network extension appliance. | Yes | 1/1 |
| DefaultGateway | IPv4 | Default gateway for the network extension appliance. | Yes | 1/1 |

For example:

XML Representation

|  |
| --- |
| <NetworkAppliance>   <Name>Appliance</Name>   <ProductionNetwork>pd-PortGroup-01</ProductionNetwork>   <ObtainIPAddressAutomatically>false</ObtainIPAddressAutomatically>   <ManualIpAddressSettingsInfoType>     <IpAddress>172.17.52.37</IpAddress>     <SubnetMask>255.255.254.0</SubnetMask>     <DefaultGateway>172.17.52.1</DefaultGateway>   </ManualIpAddressSettingsInfoType> </NetworkAppliance> |

JSON Representation

|  |
| --- |
| "NetworkAppliance": {   "Name": "Appliance",   "ProductionNetwork": "pd-PortGroup-01",   "ObtainIPAddressAutomatically": "false",   "ManualIpAddressSettingsInfoType": {     "IpAddress": "172.17.52.37",     "SubnetMask": "255.255.254.0",     "DefaultGateway": "172.17.52.1"   }  } |

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

The example below assigns the organization VDC with ID e923e20c-e114-4358-90d4-363d7de928f3 to the VMware Cloud Director tenant account that has ID b25f5f1d-a3c3-45ed-af23-9ef31a94dac7.

|  |
| --- |
| Request:  POST https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7/vCloudComputeResources    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <CloudTenantVCloudComputeResourceCreateSpec xmlns="http://www.veeam.com/ent/v1.0">     <VirtualDataCenterRef>urn:vCloud:OrgVdc:e923e20c-e114-4358-90d4-363d7de928f3.urn:vcloud:vdc:c20a16a7-2d09-4374-850d-84b1d6c9f7f3</VirtualDataCenterRef>     <UseNetworkFailoverResources>false</UseNetworkFailoverResources> </CloudTenantVCloudComputeResourceCreateSpec>    Response:  202 Accepted    Response Body:  <Task Href="http://restapiem.tech.local:9399/api/tasks/task-1" Type="Task" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Links>     <Link Href="http://restapiem.local:9399/api/tasks/task-1" Rel="Delete"/>   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>CreateCloudTenantVCloudComputeResource</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task Href="http://restapiem.local:9399/api/tasks/task-1" Type="Task" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Links>     <Link Href="http://restapiem.local:9399/api/tasks/task-1" Rel="Delete"/>   </Links>   <TaskId>task-427</TaskId>   <State>Finished</State>   <Operation>CreateCloudTenantVCloudComputeResource</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |


