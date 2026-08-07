---
title: "GET /cloud/hardwarePlans/{ID}/tenants"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_hardwareplans_id_tenants.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cloud/hardwarePlans/{ID}/tenants


Returns a resource representation of a collection of tenant accounts that are subscribed to the hardware plan with the specified ID.

Request

To get a list of tenant accounts subscribed to the hardware plan with the specified ID, send the GET HTTP request to the /cloud/hardwarePlans/{ID}/tenants resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/hardwarePlans/{ID}/tenants |

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

In the response body, the REST API returns a representation of the /cloud/hardwarePlans/{ID}/tenants resource collection.

Example

The example below returns a list of tenant accounts subscribed to the hardware plan with ID 82951b35-4581-4610-983a-e3a12aea1a8e.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/hardwarePlans/82951b35-4581-4610-983a-e3a12aea1a8e/tenants  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <CloudTenants xmlns="http://www.veeam.com/ent/v1.0">   <CloudTenant Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/6faeea03-a787-4b2d-a0e5-3fe215d50c53?format=Entity" Name="Applied Systems Company" UID="urn:veeam:CloudTenant:6faeea03-a787-4b2d-a0e5-3fe215d50c53">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudTenantReference" Href="https://localhost:9398/api/cloud/tenants/6faeea03-a787-4b2d-a0e5-3fe215d50c53" Name="Applied Systems Company" />       <Link Rel="Edit" Type="CloudTenantReference" Href="https://localhost:9398/api/cloud/tenants/6faeea03-a787-4b2d-a0e5-3fe215d50c53" Name="Applied Systems Company" />       <Link Rel="Down" Type="CloudTenantResourceList" Href="https://localhost:9398/api/cloud/tenants/6faeea03-a787-4b2d-a0e5-3fe215d50c53/resources" />       <Link Rel="Create" Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/6faeea03-a787-4b2d-a0e5-3fe215d50c53/resources" />       <Link Rel="Delete" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/6faeea03-a787-4b2d-a0e5-3fe215d50c53" Name="Applied Systems Company" />       <Link Rel="Down" Type="CloudTenantComputeResourceList" Href="https://localhost:9398/api/cloud/tenants/6faeea03-a787-4b2d-a0e5-3fe215d50c53/computeResources" />       <Link Rel="Create" Type="CloudTenantComputeResource" Href="https://localhost:9398/api/cloud/tenants/6faeea03-a787-4b2d-a0e5-3fe215d50c53/computeResources" />     </Links>     <Description>Tenant account for Applied Systems Company</Description>     <Enabled>true</Enabled>     <LeaseOptions Enabled="false" />     <Resources>       <CloudTenantResource Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/6faeea03-a787-4b2d-a0e5-3fe215d50c53/resources/82e08f60-0eef-4f28-84e7-43666d8658b8" Id="82e08f60-0eef-4f28-84e7-43666d8658b8">         <RepositoryQuota>           <DisplayName>Cloud Repository</DisplayName>           <RepositoryUid>urn:veeam:Repository:891a508a-36e4-427b-9499-8da4fba3f397</RepositoryUid>           <Quota>10240</Quota>           <UsedQuota>0</UsedQuota>         </RepositoryQuota>       </CloudTenantResource>     </Resources>     <LastResult>None</LastResult>     <LastActive>2025-01-11T01:24:51.137Z</LastActive>     <ComputeResources>       <CloudTenantComputeResource Type="CloudTenantComputeResource" Href="https://localhost:9398/api/cloud/tenants/6faeea03-a787-4b2d-a0e5-3fe215d50c53/computeResources/9394795a-c9e5-4193-be33-00f1aedbfa50" Id="9394795a-c9e5-4193-be33-00f1aedbfa50">         <CloudHardwarePlanUid>urn:veeam:CloudHardwarePlan:82951b35-4581-4610-983a-e3a12aea1a8e</CloudHardwarePlanUid>         <PlatformType>HyperV</PlatformType>         <UseNetworkFailoverResources>false</UseNetworkFailoverResources>         <ComputeResourceStats>           <MemoryUsageMb>0</MemoryUsageMb>           <CPUCount>0</CPUCount>           <StorageResourceStats>             <StorageResourceStat>               <StorageName>Cloud Replicas</StorageName>               <StorageUsageGb>0</StorageUsageGb>               <StorageLimitGb>100</StorageLimitGb>             </StorageResourceStat>           </StorageResourceStats>         </ComputeResourceStats>       </CloudTenantComputeResource>     </ComputeResources>     <ThrottlingEnabled>false</ThrottlingEnabled>     <ThrottlingSpeedLimit>1</ThrottlingSpeedLimit>     <ThrottlingSpeedUnit>MBps</ThrottlingSpeedUnit>     <PublicIpCount>0</PublicIpCount>     <BackupCount>0</BackupCount>     <ReplicaCount>0</ReplicaCount>   </CloudTenant>   <CloudTenant Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/4e507777-8349-4683-9336-5fd1ecc27ea6?format=Entity" Name="UCM Company" UID="urn:veeam:CloudTenant:4e507777-8349-4683-9336-5fd1ecc27ea6">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudTenantReference" Href="https://localhost:9398/api/cloud/tenants/4e507777-8349-4683-9336-5fd1ecc27ea6" Name="UCM Company" />       <Link Rel="Edit" Type="CloudTenantReference" Href="https://localhost:9398/api/cloud/tenants/4e507777-8349-4683-9336-5fd1ecc27ea6" Name="UCM Company" />       <Link Rel="Down" Type="CloudTenantResourceList" Href="https://localhost:9398/api/cloud/tenants/4e507777-8349-4683-9336-5fd1ecc27ea6/resources" />       <Link Rel="Create" Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/4e507777-8349-4683-9336-5fd1ecc27ea6/resources" />       <Link Rel="Delete" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/4e507777-8349-4683-9336-5fd1ecc27ea6" Name="UCM Company" />       <Link Rel="Down" Type="CloudTenantComputeResourceList" Href="https://localhost:9398/api/cloud/tenants/4e507777-8349-4683-9336-5fd1ecc27ea6/computeResources" />       <Link Rel="Create" Type="CloudTenantComputeResource" Href="https://localhost:9398/api/cloud/tenants/4e507777-8349-4683-9336-5fd1ecc27ea6/computeResources" />     </Links>     <Description>Tenant account for UCM Company</Description>     <Enabled>true</Enabled>     <LeaseOptions Enabled="false" />     <Resources>       <CloudTenantResource Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/4e507777-8349-4683-9336-5fd1ecc27ea6/resources/1d4fc6c4-9853-450a-a2a9-646cdb8c5c72" Id="1d4fc6c4-9853-450a-a2a9-646cdb8c5c72">         <RepositoryQuota>           <DisplayName>Cloud Repository 1</DisplayName>           <RepositoryUid>urn:veeam:Repository:891a508a-36e4-427b-9499-8da4fba3f397</RepositoryUid>           <Quota>102400</Quota>           <UsedQuota>20609</UsedQuota>         </RepositoryQuota>       </CloudTenantResource>     </Resources>     <LastResult>None</LastResult>     <LastActive>2025-01-11T01:24:51.137Z</LastActive>     <ComputeResources>       <CloudTenantComputeResource Type="CloudTenantComputeResource" Href="https://localhost:9398/api/cloud/tenants/4e507777-8349-4683-9336-5fd1ecc27ea6/computeResources/93d89cff-53c0-4f50-b987-e2d064d9d45c" Id="93d89cff-53c0-4f50-b987-e2d064d9d45c">         <CloudHardwarePlanUid>urn:veeam:CloudHardwarePlan:82951b35-4581-4610-983a-e3a12aea1a8e</CloudHardwarePlanUid>         <PlatformType>HyperV</PlatformType>         <UseNetworkFailoverResources>true</UseNetworkFailoverResources>         <NetworkAppliance>           <Name>UCM Company Appliance</Name>           <ProductionNetwork>Intel(R) I350 Gigabit Network Connection - Virtual Switch</ProductionNetwork>           <ObtainIPAddressAutomatically>true</ObtainIPAddressAutomatically>         </NetworkAppliance>         <ComputeResourceStats>           <MemoryUsageMb>4096</MemoryUsageMb>           <CPUCount>1</CPUCount>           <StorageResourceStats>             <StorageResourceStat>               <StorageName>Cloud Replicas</StorageName>               <StorageUsageGb>17</StorageUsageGb>               <StorageLimitGb>100</StorageLimitGb>             </StorageResourceStat>           </StorageResourceStats>         </ComputeResourceStats>       </CloudTenantComputeResource>     </ComputeResources>     <ThrottlingEnabled>false</ThrottlingEnabled>     <ThrottlingSpeedLimit>1</ThrottlingSpeedLimit>     <ThrottlingSpeedUnit>MBps</ThrottlingSpeedUnit>     <PublicIpCount>0</PublicIpCount>     <BackupCount>0</BackupCount>     <ReplicaCount>1</ReplicaCount>   </CloudTenant> </CloudTenants> |

Page updated 2026-07-29

