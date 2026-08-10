---
title: "GET /query?type=CloudTenant"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_cloudtenant.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=CloudTenant


Returns a resource representation of a collection of tenant accounts created on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/cloud/tenants](tenants.md).

Request

To get a list of tenant accounts, send the GET HTTP request to the query with the type parameter set to CloudTenant.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=CloudTenant |

Request Headers

The request contains the following headers:

Request Headers

| Header | Required | Description |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Optional Parameters

In the query, you can use the following parameters for filtering and sorting.

Optional Parameters

| Parameter | Type | Description |
| UID | UidType | UID of the tenant account, for example: urn:veeam:CloudTenant:4f90635a-7ecc-49fe-beb6-60b37eb4bd89. |
| Name | String | Name or the tenant account, for example: Cloud Tenant. |
| Enabled | Boolean | Defines if the tenant account is in the enabled or disabled state. Possible values:   * True * False |
| BackupServerUId | UidType | UID of the backup server parent to the tenant resource. |
| BackupServerName | String | Name of the backup server parent to the tenant resource. |
| Type | CloudTenantType | Tenant account type. Possible values:   * vCD * Standalone * ActiveDirectory |
| OrganizationReference | HierarchyObjRefType | Reference to the vCD organization whose resources are provided to the VMware Cloud Director tenant account. The reference can be [constructed manually](constructing_hierarchyobjreftype.md) or obtained with the lookup service. For details on using the lookup, see [Virtual Infrastructure Lookup](lookup_service.md). |

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

In the response body, the REST API returns a representation of the /cloud/tenants resource collection.

Example

The example below returns an entity resource representation of a collection of Active Directory tenant accounts created on the 172.24.31.67 backup server. The results are ordered in the acceding order by the Name parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=CloudTenant&format=Entities&sortAsc=name&filter=BackupServerName=="172.24.31.67";Type==ActiveDirectory  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <CloudTenants>       <CloudTenant Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/9c3aad22-3d96-43fe-ab25-6e1800b0dda0?format=Entity" Name="tech\john.smith" UID="urn:veeam:CloudTenant:9c3aad22-3d96-43fe-ab25-6e1800b0dda0">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ca19249e-e638-421a-ab22-68cb89b9009a" Name="172.24.31.67" />           <Link Rel="Alternate" Type="CloudTenantReference" Href="https://localhost:9398/api/cloud/tenants/9c3aad22-3d96-43fe-ab25-6e1800b0dda0" Name="tech\john.smith" />           <Link Rel="Edit" Type="CloudTenantReference" Href="https://localhost:9398/api/cloud/tenants/9c3aad22-3d96-43fe-ab25-6e1800b0dda0" Name="tech\john.smith" />           <Link Rel="Down" Type="CloudTenantResourceList" Href="https://localhost:9398/api/cloud/tenants/9c3aad22-3d96-43fe-ab25-6e1800b0dda0/resources" />           <Link Rel="Create" Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/9c3aad22-3d96-43fe-ab25-6e1800b0dda0/resources" />           <Link Rel="Delete" Href="https://localhost:9398/api/cloud/tenants/9c3aad22-3d96-43fe-ab25-6e1800b0dda0" />           <Link Rel="Related" Type="FreeLicenseCounters" Href="https://localhost:9398/api/cloud/tenants/9c3aad22-3d96-43fe-ab25-6e1800b0dda0/freelicenseCounters" Name="FreeLicenseCounters" />         </Links>         <Description>Tenant account for AD user</Description>         <Enabled>true</Enabled>         <LeaseOptions Enabled="false" />         <Resources>           <CloudTenantResource Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/9c3aad22-3d96-43fe-ab25-6e1800b0dda0/resources/6022432d-375f-46a8-bea4-b28ab2ad8bd5" Id="6022432d-375f-46a8-bea4-b28ab2ad8bd5">             <RepositoryQuota>               <DisplayName>AD User Cloud Repository</DisplayName>               <RepositoryUid>urn:veeam:Repository:003a6ffe-b9f5-4e37-9aa8-27c468d827da</RepositoryUid>               <WanAcceleratorUid>urn:veeam:WanAccelerator:3a2a5b97-6248-4b62-8310-e57239ecd44e</WanAcceleratorUid>               <Quota>30720</Quota>               <UsedQuota>0</UsedQuota>             </RepositoryQuota>           </CloudTenantResource>         </Resources>         <LastResult>Success</LastResult>         <ComputeResources />         <ThrottlingEnabled>true</ThrottlingEnabled>         <ThrottlingSpeedLimit>10</ThrottlingSpeedLimit>         <ThrottlingSpeedUnit>MBps</ThrottlingSpeedUnit>         <PublicIpCount>0</PublicIpCount>         <BackupCount>0</BackupCount>         <ReplicaCount>0</ReplicaCount>         <MaxConcurrentTasks>1</MaxConcurrentTasks>         <WorkStationBackupCount>0</WorkStationBackupCount>         <ServerBackupCount>0</ServerBackupCount>         <BackupProtectionEnabled>true</BackupProtectionEnabled>         <BackupProtectionPeriod>1</BackupProtectionPeriod>         <TenantType>           <ADTenantType>             <Domain>               <DomainName>tech.local</DomainName>               <DomainAccount>f1b5f006-5e29-4702-8aaa-7653d30af191</DomainAccount>               <Port>389</Port>             </Domain>             <Account>tech\john.smith</Account>           </ADTenantType>         </TenantType>       </CloudTenant>       <CloudTenant Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/9d35e68b-3c54-4e85-8a77-c0a2d8b069ed?format=Entity" Name="tech\william.fox" UID="urn:veeam:CloudTenant:9d35e68b-3c54-4e85-8a77-c0a2d8b069ed">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ca19249e-e638-421a-ab22-68cb89b9009a" Name="172.24.31.67" />           <Link Rel="Alternate" Type="CloudTenantReference" Href="https://localhost:9398/api/cloud/tenants/9d35e68b-3c54-4e85-8a77-c0a2d8b069ed" Name="tech\william.fox" />           <Link Rel="Edit" Type="CloudTenantReference" Href="https://localhost:9398/api/cloud/tenants/9d35e68b-3c54-4e85-8a77-c0a2d8b069ed" Name="tech\william.fox" />           <Link Rel="Down" Type="CloudTenantResourceList" Href="https://localhost:9398/api/cloud/tenants/9d35e68b-3c54-4e85-8a77-c0a2d8b069ed/resources" />           <Link Rel="Create" Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/9d35e68b-3c54-4e85-8a77-c0a2d8b069ed/resources" />           <Link Rel="Delete" Href="https://localhost:9398/api/cloud/tenants/9d35e68b-3c54-4e85-8a77-c0a2d8b069ed" />           <Link Rel="Related" Type="FreeLicenseCounters" Href="https://localhost:9398/api/cloud/tenants/9d35e68b-3c54-4e85-8a77-c0a2d8b069ed/freelicenseCounters" Name="FreeLicenseCounters" />         </Links>         <Description>Tenant account for AD user</Description>         <Enabled>true</Enabled>         <LeaseOptions Enabled="false" />         <Resources>           <CloudTenantResource Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/9d35e68b-3c54-4e85-8a77-c0a2d8b069ed/resources/7c5a1a30-6478-4c99-9412-dae65f3b6a5f" Id="7c5a1a30-6478-4c99-9412-dae65f3b6a5f">             <RepositoryQuota>               <DisplayName>Cloud repository 1</DisplayName>               <RepositoryUid>urn:veeam:Repository:5236d23a-c8a9-4bbf-9e4a-26b4c63e339d</RepositoryUid>               <WanAcceleratorUid>urn:veeam:WanAccelerator:3a2a5b97-6248-4b62-8310-e57239ecd44e</WanAcceleratorUid>               <Quota>10240</Quota>               <UsedQuota>0</UsedQuota>             </RepositoryQuota>           </CloudTenantResource>         </Resources>         <LastResult>Success</LastResult>         <ComputeResources />         <ThrottlingEnabled>false</ThrottlingEnabled>         <ThrottlingSpeedLimit>1</ThrottlingSpeedLimit>         <ThrottlingSpeedUnit>MBps</ThrottlingSpeedUnit>         <PublicIpCount>0</PublicIpCount>         <BackupCount>0</BackupCount>         <ReplicaCount>0</ReplicaCount>         <MaxConcurrentTasks>1</MaxConcurrentTasks>         <WorkStationBackupCount>0</WorkStationBackupCount>         <ServerBackupCount>0</ServerBackupCount>         <BackupProtectionEnabled>false</BackupProtectionEnabled>         <BackupProtectionPeriod>1</BackupProtectionPeriod>         <TenantType>           <ADTenantType>             <Domain>               <DomainName>tech.local</DomainName>               <DomainAccount>f1b5f006-5e29-4702-8aaa-7653d30af191</DomainAccount>               <Port>389</Port>             </Domain>             <Account>tech\william.fox</Account>           </ADTenantType>         </TenantType>       </CloudTenant>     </CloudTenants>   </Entities>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=CloudTenant&format=Entities&sortAsc=name&filter=BackupServerName=="172.24.31.67";Type==ActiveDirectory&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=CloudTenant&format=Entities&sortAsc=name&filter=BackupServerName=="172.24.31.67";Type==ActiveDirectory&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

