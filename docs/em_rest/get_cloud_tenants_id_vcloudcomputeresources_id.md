---
title: "GET /cloud/tenants/{ID}/vCloudComputeResources/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cloud_tenants_id_vcloudcomputeresources_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# GET /cloud/tenants/{ID}/vCloudComputeResources/{ID}


Returns an organization VDC with the specified ID that is assigned to a VMware Cloud Director tenant account with the specified ID.

Request

To get an organization VDC that is assigned to the VMware Cloud Director tenant account, send the GET HTTP request to the /cloud/tenants/{ID}/vCloudComputeResources/{ID} resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}/vCloudComputeResources/{ID} |

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

In the response body, the REST API returns a representation of the /cloud/tenants/{ID}/vCloudComputeResources/{ID} resource that contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| VirtualDataCenterName | String | Name of the organization virtual datacenter. |
| VirtualDataCenterRef | HierarchyObjRefType | Reference to the the organization virtual datacenter. For example: urn:vCloud:Organization:36a46edd-ae1a-4f5b-9557-36fb66f45510.urn:vcloud:vdc:abb1d2f8-86d9-4804-9184-250d4f59a9a8. |
| Enabled | Boolean | Defines whether the organization virtual datacenter is enabled. Possible values:   * True * False |
| AllocationModel | String | Allocation model. Possible values:   * Unknown * AllocationPool * PayAsYouGo * ReservationPool * Flex |
| UseNetworkFailoverResources | Boolean | Defines whether the network extension appliance must be deployed for the VMware Cloud Director tenant account. Possible values:   * True * False |
| ResourceUsage | CloudTenantVCloudCompute | Statistics on usage of the compute resources by the VMware Cloud Director tenant. For details, see [vCD Compute Resource Statistics](#vCDComputeResourceStatistics). |
| WanAcceleratorUid | UidType | UID of the WAN accelerator that must be used as a target WAN accelerator. This parameter must be specified if you want tenants to communicate with vCloud hosts through WAN accelerators. |
| NetworkAppliance | NetworkApplianceInfoType | If UseNetworkFailoverResources option is set to True, you can pass parameters for the network extension appliance in the NetworkAppliance section of the request body. For details, see [Network Extension Options](#appliance). |

vCD Compute Resource Statistics

The ResourceUsage element contains the following statistics on usage of the compute resources by the VMware Cloud Director tenant.

| Element | Type | Description |
| --- | --- | --- |
| CpuUsageMhz | Int | Amount of CPU used by the tenant. |
| MemoryUsageMb | Int | Amount of memory used by the tenant. |
| StorageUsageGb | Int | Amount of disc space used by the tenant. |

Network Extension Options

The NetworkAppliance element contains the following network extension options.

| Element | Type | Description |
| --- | --- | --- |
| Name | String | Name for the network extension appliance. |
| ProductionNetwork | String | Network label that identifies the port group to which the network extension appliance is connected. The port group is configured on the virtual switch in the SP virtualization environment and provides networking for the Veeam Cloud Connect infrastructure. |
| ObtainIpAddressAutomatically | Boolean | Defines whether network settings must be configured automatically for the network extension appliance. Possible values:   * True * False |
| ManualIpAddressSettingsInfoType | ManualIpAddressSettingsInfoType | Network settings for the network extension appliance. For details, see [Manual Ip Addressing Options](#ip). |
| ViDistributedSwitchUuid | String | UID of the Distributed Virtual Switch on which the port group specified in the ProductionNetwork field is configured. |
| ProductionNetworkUnderDvs | Boolean | Defines whether the port group to which the network extension appliance is connected is configured on a Distributed Virtual Switch. Possible values:   * True * False |

Manual IP Addressing Options

The ObtainIpAddressAutomatically element contains the following manual IP addressing options.

| Element | Type | Description |
| --- | --- | --- |
| IpAddress | IPv4 | IP address for the network extension appliance. |
| SubnetMask | IPv4 | Subnet mask for the network extension appliance. |
| DefaultGateway | IPv4 | Default gateway for the network extension appliance. |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /cloud/tenants/{ID}/cCloudComputeResources/{ID} | Delete | URL for the [DELETE /cloud/tenants/{ID}/vCloudComputeResources/{ID}](delete_cloud_tenants_id_vcloudcomputeresources_id.md) request. |
| /cloud/tenants/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a tenant subscribed to the compute resource. |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server of the service provider. |

Example

The example below returns an organization VDC with ID c20a16a7-2d09-4374-850d-84b1d6c9f7f3 that is assigned to the tenant account with ID 59aa38fb-aa88-4656-bc52-d31e8f85083e.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/tenants/59aa38fb-aa88-4656-bc52-d31e8f85083e/vCloudComputeResources/c20a16a7-2d09-4374-850d-84b1d6c9f7f3    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <CloudTenantVCloudComputeResource Href="http://local.host:9399/api/cloud/tenants/59aa38fb-aa88-4656-bc52-d31e8f85083e/vcloudcomputeresources/c20a16a7-2d09-4374-850d-84b1d6c9f7f3" Type="CloudTenantVCloudComputeResource" Id="c20a16a7-2d09-4374-850d-84b1d6c9f7f3" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> |


