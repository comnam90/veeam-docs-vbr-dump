---
title: "GET /cloud/tenants/{ID}/computeResources"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_tenants_id_computeresources.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cloud/tenants/{ID}/computeResources


Returns a collection of hardware plans to which the tenant account with the specified ID is subscribed.

Request

To get a list of hardware plans to which the tenant is subscribed, send the GET HTTP request to the /cloud/tenants/{ID}/computeResources resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}/computeResources |

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

In the response body, the REST API returns a representation of the /cloud/tenants/{ID}/computeResources resource.

Example

The example below returns hardware plans for the tenant account with ID b25f5f1d-a3c3-45ed-af23-9ef31a94dac7.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7/resources  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <CloudTenantComputeResources xmlns="http://www.veeam.com/ent/v1.0">   <CloudTenantComputeResource Type="CloudTenantComputeResource" Href="https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7/computeResources/25f485fd-06e3-4ee2-9703-465c4d8c2fae" Id="25f485fd-06e3-4ee2-9703-465c4d8c2fae">     <Links>       <Link Rel="Delete" Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7/computeResources/25f485fd-06e3-4ee2-9703-465c4d8c2fae" Name="" />       <Link Rel="Up" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7?format=Entity" Name="ABC Company" />       <Link Rel="Up" Type="BackupServer" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982?format=Entity" Name="172.17.53.48" />     </Links>     <CloudHardwarePlanUid>urn:veeam:CloudHardwarePlan:91156f8d-8bd3-44af-bec3-b6ac2ea24288</CloudHardwarePlanUid>     <WanAcceleratorUid>urn:veeam:WanAccelerator:34ebeeb4-75d0-4e71-b315-fbc16eb2975f</WanAcceleratorUid>     <PlatformType>VMware</PlatformType>     <UseNetworkFailoverResources>true</UseNetworkFailoverResources>     <NetworkAppliance>       <Name>Cloud Appliance ABC Company(esx01)</Name>       <ProductionNetwork>VM Network</ProductionNetwork>       <ObtainIPAddressAutomatically>true</ObtainIPAddressAutomatically>       <ViDistributedSwitchUuid/>     </NetworkAppliance>     <ComputeResourceStats>       <MemoryUsageMb>8192</MemoryUsageMb>       <CPUCount>2</CPUCount>       <StorageResourceStats>         <StorageResourceStat>           <StorageName>Cloud Replicas</StorageName>           <StorageUsageGb>35</StorageUsageGb>           <StorageLimitGb>300</StorageLimitGb>         </StorageResourceStat>       </StorageResourceStats>     </ComputeResourceStats>   </CloudTenantComputeResource> </CloudTenantComputeResources> |

Page updated 2026-07-29

