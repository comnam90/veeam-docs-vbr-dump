---
title: "GET /cloud/tenants/{ID}/computeResources/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_tenants_id_computeresources_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a hardware plan with the specified ID to which the tenant account with the specified ID is subscribed.

Request

To get a hardware plan to which the tenant account is subscribed, send the GET HTTP request to the /cloud/tenants/{ID}/computeResources/{ID} resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}/computeResources/{ID} |

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

In the response body, the REST API returns a representation of the /cloud/tenants/{ID}/computeResources/{ID} resource that contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| CloudHardwarePlanUid | UidType | UID of the hardware plan to which the tenant account is subscribed. |
| WanAcceleratorUid | UidType | UID of the WAN accelerator used as a target WAN accelerator with the cloud host presented by the hardware plan. |
| PlatformType | String | Platform for which the tenant hardware plan has been created. Possible values:   * VMware * HyperV |
| UseNetworkFailoverResources | Boolean | Defines whether the network extension appliance must be deployed for the tenant account subscribed to the hardware plan. Possible values:   * True * False |
| NetworkAppliance | NetworkApplianceInfoType | Settings for the network extension appliance. For details, see [Network Extension Options](#appliance). |
| ComputeResourceStats | ComputeResourceStatsInfoType | Statistics of the compute resource. For details, see [Compute Resource Statistics](#ComputeResourceStatistics). |

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

Compute Resource Statistics

The ComputeResourceStats element contains the following  statistics on usage of the compute resources by the tenant.

| Element | Type | Description |
| --- | --- | --- |
| IpAddress | IPv4 | Amount of memory used by the tenant. |
| SubnetMask | IPv4 | Number of CPUs used by the tenant. |
| DefaultGateway | IPv4 | Statistics on storage usage. For details, see [Storage Resource Statistics](#StorageResourceStatistics). |

Storage Resource Statistics

The StorageResourceStats element contains the following statistics on storage usage.

| Element | Type | Description |
| --- | --- | --- |
| StorageName | String | Name of the storage where tenant VM replicas are stored. |
| StorageUsageGb | Int | Number of CPUs used by the tenant. |
| StorageLimitGb | Int | Maximum amount of disc space that can be used by the tenant. |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /cloud/tenants/{ID}/computeResources/{ID} | Delete | URL for the [DELETE /cloud/tenants/{ID}/computeResources/{ID}](delete_tenants_id_computeresources_id.md) request. |
| /cloud/tenants/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a tenant subscribed to the compute resource. |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server of the service provider. |

Example

The example below returns a hardware plan with ID 25f485fd-06e3-4ee2-9703-465c4d8c2fae to which the tenant account with ID b25f5f1d-a3c3-45ed-af23-9ef31a94dac7 is subscribed.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7/computeResources/25f485fd-06e3-4ee2-9703-465c4d8c2fae    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <CloudTenantComputeResource xmlns="http://www.veeam.com/ent/v1.0" Type="CloudTenantComputeResource" Href="https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7/computeResources/25f485fd-06e3-4ee2-9703-465c4d8c2fae" Id="25f485fd-06e3-4ee2-9703-465c4d8c2fae"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
