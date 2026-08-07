---
title: "GET /query?type=CloudSubtenant"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_cloudsubtenant.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=CloudSubtenant


Returns a list of subtenant accounts created for tenant accounts. For details, see [/cloud/tenants/{ID}/subtenants](tenants_id_subtenants.md).

Request

To get a list of subtenant accounts, send the GET HTTP request to the query with the type parameter set to CloudSubtenant.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=CloudSubtenant |

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
| UID | String | ID of the subtenant account resource, for example: 4da30260-581d-4b94-8a56-61c117819dcc. |
| Name | String | Name of the subtenant account, for example: ABC Company PC User. |
| CloudTenantUid | UidType | UID of the tenant account parent to the subtenant account resource, for example: urn:veeam:CloudTenant:65f1c495-1942-449b-8317-e877251d0822. |
| CloudTenantName | String | Name of the tenant account parent to the subtenant account resource, for example: ABC Company. |
| Disabled | Boolean | Defines whether the subtenant account is in the disabled or enabled state. Possible values:   * True — the subtenant account is disabled * False — the subtenant account is enabled |
| Unlimited | Boolean | Defines whether the storage quota assigned to the subtenant account is unlimited. Possible values:   * True — the subtenant quota is not limited. The subtenant can use all storage space available within the tenant quota. * False — the subtenant quota is limited. |
| Quota | Int | Size of the storage quota assigned to the subtenant account (in MB). |
| UsedQuota | Int | Amount of used space within the storage quota assigned to the subtenant account (in MB). |
| BackupResourceId | String | ID of the tenant storage quota on which the storage quota for the subtenant account is created, for example: 11c59670-23df-448c-a4b3-74c42669633e. |
| BackupServerUID | UidType | UID of the backup server parent to the subtenant account resource. |
| BackupServerName | String | Name of the backup server parent to the subtenant account resource. |

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

In the response body, the REST API returns a representation of the /cloud/tenants/{ID}/subtenants resource collection.

Example

The example below returns an entity resource representation of a collection of enabled subtenant accounts created for the ABC Company tenant on the 172.24.31.67 backup server. The results are ordered in the acceding order by the Name parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=CloudSubtenant&format=Entities&sortAsc=Name&filter=BackupServerName=="172.24.31.67";Disabled==false;CloudTenantName=="ABC Company"  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Resources>     <CloudSubtenants>       <CloudSubtenant Type="CloudSubtenant" Href="https://localhost:9398/api/cloud/tenants/e38a8692-6816-443e-9052-7fa71ee7fd65/subtenants/5f6a393a-e80b-4b20-91f0-db47b6a7dcbe" Id="5f6a393a-e80b-4b20-91f0-db47b6a7dcbe">         <Links>           <Link Rel="Edit" Type="CloudSubtenant" Href="https://localhost:9398/api/cloud/tenants/e38a8692-6816-443e-9052-7fa71ee7fd65/subtenants/5f6a393a-e80b-4b20-91f0-db47b6a7dcbe" Name="User01" />           <Link Rel="Delete" Href="https://localhost:9398/api/cloud/tenants/e38a8692-6816-443e-9052-7fa71ee7fd65/subtenants/5f6a393a-e80b-4b20-91f0-db47b6a7dcbe" />           <Link Rel="Up" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/e38a8692-6816-443e-9052-7fa71ee7fd65?format=Entity" Name="ABC Company" />           <Link Rel="Up" Type="BackupServer" Href="https://localhost:9398/api/backupServers/ca19249e-e638-421a-ab22-68cb89b9009a?format=Entity" Name="172.24.31.67" />         </Links>         <Name>User01</Name>         <Description />         <Password />         <Enabled>true</Enabled>         <RepositoryQuota Unlimited="true">           <DisplayName>User01</DisplayName>           <TenantResourceId>502686fc-44ea-4f8b-b5f6-7c11a90aa12d</TenantResourceId>           <QuotaMb>1024</QuotaMb>           <UsedQuotaMb>0</UsedQuotaMb>           <QuotaId>52a1705e-cb79-481c-9209-245b12e17089</QuotaId>         </RepositoryQuota>       </CloudSubtenant>       <CloudSubtenant Type="CloudSubtenant" Href="https://localhost:9398/api/cloud/tenants/e38a8692-6816-443e-9052-7fa71ee7fd65/subtenants/9e924fbb-54d5-4bab-82e0-68216d45b096" Id="9e924fbb-54d5-4bab-82e0-68216d45b096">         <Links>           <Link Rel="Edit" Type="CloudSubtenant" Href="https://localhost:9398/api/cloud/tenants/e38a8692-6816-443e-9052-7fa71ee7fd65/subtenants/9e924fbb-54d5-4bab-82e0-68216d45b096" Name="User03" />           <Link Rel="Delete" Href="https://localhost:9398/api/cloud/tenants/e38a8692-6816-443e-9052-7fa71ee7fd65/subtenants/9e924fbb-54d5-4bab-82e0-68216d45b096" />           <Link Rel="Up" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/e38a8692-6816-443e-9052-7fa71ee7fd65?format=Entity" Name="ABC Company" />           <Link Rel="Up" Type="BackupServer" Href="https://localhost:9398/api/backupServers/ca19249e-e638-421a-ab22-68cb89b9009a?format=Entity" Name="172.24.31.67" />         </Links>         <Name>User03</Name>         <Description>Created by SRV12\Administrator at 7/31/2025 9:28 PM.</Description>         <Password />         <Enabled>true</Enabled>         <RepositoryQuota Unlimited="true">           <DisplayName>User03 Quota</DisplayName>           <TenantResourceId>502686fc-44ea-4f8b-b5f6-7c11a90aa12d</TenantResourceId>           <QuotaMb>10240</QuotaMb>           <UsedQuotaMb>0</UsedQuotaMb>           <QuotaId>321cbe67-cc8c-474e-ab1e-2694311ef794</QuotaId>         </RepositoryQuota>       </CloudSubtenant>       <CloudSubtenant Type="CloudSubtenant" Href="https://localhost:9398/api/cloud/tenants/e38a8692-6816-443e-9052-7fa71ee7fd65/subtenants/24fd5279-060e-48c5-9ad2-070d823bc705" Id="24fd5279-060e-48c5-9ad2-070d823bc705">         <Links>           <Link Rel="Edit" Type="CloudSubtenant" Href="https://localhost:9398/api/cloud/tenants/e38a8692-6816-443e-9052-7fa71ee7fd65/subtenants/24fd5279-060e-48c5-9ad2-070d823bc705" Name="User2" />           <Link Rel="Delete" Href="https://localhost:9398/api/cloud/tenants/e38a8692-6816-443e-9052-7fa71ee7fd65/subtenants/24fd5279-060e-48c5-9ad2-070d823bc705" />           <Link Rel="Up" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/e38a8692-6816-443e-9052-7fa71ee7fd65?format=Entity" Name="ABC Company" />           <Link Rel="Up" Type="BackupServer" Href="https://localhost:9398/api/backupServers/ca19249e-e638-421a-ab22-68cb89b9009a?format=Entity" Name="172.24.31.67" />         </Links>         <Name>User2</Name>         <Description>Created by SRV13\Administrator at 7/19/2025 9:11 PM.</Description>         <Password />         <Enabled>true</Enabled>         <RepositoryQuota Unlimited="true">           <DisplayName>Quota</DisplayName>           <TenantResourceId>502686fc-44ea-4f8b-b5f6-7c11a90aa12d</TenantResourceId>           <QuotaMb>10240</QuotaMb>           <UsedQuotaMb>0</UsedQuotaMb>           <QuotaId>4f8d70ba-6434-4f47-9883-67874b8f334f</QuotaId>         </RepositoryQuota>       </CloudSubtenant>     </CloudSubtenants>   </Resources>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=CloudSubtenant&format=Entities&sortAsc=Name&filter=BackupServerName=="172.24.31.67";Disabled==false;CloudTenantName=="ABC+Company"&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=CloudSubtenant&format=Entities&sortAsc=Name&filter=BackupServerName=="172.24.31.67";Disabled==false;CloudTenantName=="ABC+Company"&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

