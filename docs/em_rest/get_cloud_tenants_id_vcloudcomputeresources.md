---
title: "GET /cloud/tenants/{ID}/vCloudComputeResources"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cloud_tenants_id_vcloudcomputeresources.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cloud/tenants/{ID}/vCloudComputeResources


Returns a list of organization vDCs for the VMware Cloud Director tenant account with the specified ID.

Request

To get a list of organization vDCs assigned to the VMware Cloud Director tenant account, send the GET HTTP request to the /cloud/tenants/{ID}/vCloudComputeResources resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}/vCloudComputeResources |

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

In the response body, the REST API returns a representation of the /cloud/tenants/{ID}/vCloudComputeResources resource.

Example

The example below returns organization vDCs for the tenant account with ID b25f5f1d-a3c3-45ed-af23-9ef31a94dac7.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7/vCloudComputeResources  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <CloudTenantVCloudComputeResource Href="http://restapiem.local:9399/api/cloud/tenants/59aa38fb-aa88-4656-bc52-d31e8f85083e/vcloudcomputeresources/c20a16a7-2d09-4374-850d-84b1d6c9f7f3" Type="CloudTenantVCloudComputeResource" Id="c20a16a7-2d09-4374-850d-84b1d6c9f7f3" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Links>     <Link Href="http://restapiem.local:9399/api/cloud/tenants/59aa38fb-aa88-4656-bc52-d31e8f85083e/vcloudcomputeresources/c20a16a7-2d09-4374-850d-84b1d6c9f7f3" Rel="Delete"/>     <Link Href="http://restapiem.local:9399/api/cloud/tenants/59aa38fb-aa88-4656-bc52-d31e8f85083e?format=Entity" Name="restapi" Type="CloudTenant" Rel="Up"/>     <Link Href="http://restapiem.local:9399/api/backupServers/6b6456ca-68ac-4559-a0e9-808bb519082f?format=Entity" Name="restapivbr.local" Type="BackupServer" Rel="Up"/>   </Links>   <VirtualDataCenterName>restapivdc01</VirtualDataCenterName>   <VirtualDataCenterRef>urn:vCloud:OrgVdc:1e902b80-e842-41e6-a4bf-4cf153c53e5c.urn:vcloud:vdc:c20a16a7-2d09-4374-850d-84b1d6c9f7f3</VirtualDataCenterRef>   <Enabled>true</Enabled>   <AllocationModel>AllocationPool</AllocationModel>   <UseNetworkFailoverResources>true</UseNetworkFailoverResources>   <ResourceUsage>     <CpuUsageMhz>0</CpuUsageMhz>     <MemoryUsageMb>0</MemoryUsageMb>     <StorageUsageGb>0</StorageUsageGb>   </ResourceUsage>   <WanAcceleratorUid>urn:veeam:WanAccelerator:9253bc8b-ab04-4f48-be35-08c81795d2e5</WanAcceleratorUid>   <NetworkAppliance>     <Name>Network Extension Appliance</Name>     <ProductionNetwork>VM Network</ProductionNetwork>     <ObtainIPAddressAutomatically>true</ObtainIPAddressAutomatically>     <ViDistributedSwitchUuid/>     <ProductionNetworkUnderDvs>false</ProductionNetworkUnderDvs>   </NetworkAppliance> </CloudTenantVCloudComputeResource> |

Page updated 2026-07-29

