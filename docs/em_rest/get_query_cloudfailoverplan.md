---
title: "GET /query?type=CloudFailoverPlan"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_cloudfailoverplan.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=CloudFailoverPlan


Returns a resource representation of a collection of cloud failover plans configured by tenants on backup servers that are connected to Veeam Backup Enterprise Manager. For details, see [/cloud/cloudFailoverPlans](cloudfailoverplans.md).

Request

To get a list of cloud failover plans configured by tenants on backup servers, send the GET HTTP request to the query with the type parameter set to CloudFailoverPlan.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=CloudFailoverPlan |

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
| UID | UidType | UID of the failover plan, for example: urn:veeam:FailoverPlan:ae01e36f-32a3-4095-95fa-09a2af744009. |
| Name | String | Name of the failover plan, for example: SQL Failover Plan. |
| Description | String | Description of the failover plan specified at the time of the failover plan creation. |
| CloudTenantUid | UidType | UID of the cloud tenant account, for example: urn:veeam:CloudTenant:4f90635a-7ecc-49fe-beb6-60b37eb4bd89 |
| CloudTenantName | String | Name or the cloud tenant account, for example: Cloud Tenant. |
| BackupServerUid | UidType | UID of the backup server parent to the failover plan resource. |
| BackupServerName | String | Name of the backup server parent to the failover plan resource. |

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

In the response body, the REST API returns a representation of the /cloud/cloudFailoverPlans resource collection.

Example

The example below returns an entity resource representation of a collection of cloud failover plans configured by the ABC Company tenant created on the 172.24.31.67 backup server. The results are ordered in the acceding order by the Name parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=CloudFailoverPlan&format=Entities&sortAsc=Name&filter=BackupServerName=="172.24.31.67";CloudTenantName=="ABC Company"  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <CloudFailoverPlans>       <CloudFailoverPlan Type="CloudFailoverPlan" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/3f56fa52-c902-4655-9774-2025fde214d2?format=Entity" Name="ABC Company Failover Plan" UID="urn:veeam:CloudFailoverPlan:3f56fa52-c902-4655-9774-2025fde214d2">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ca19249e-e638-421a-ab22-68cb89b9009a" Name="172.24.31.67" />           <Link Rel="Alternate" Type="CloudFailoverPlanReference" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/3f56fa52-c902-4655-9774-2025fde214d2" Name="ABC Company Failover Plan" />           <Link Rel="Edit" Type="CloudFailoverPlanReference" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/3f56fa52-c902-4655-9774-2025fde214d2" Name="ABC Company Failover Plan" />           <Link Rel="Start" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/3f56fa52-c902-4655-9774-2025fde214d2?action=start" />           <Link Rel="Test" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/3f56fa52-c902-4655-9774-2025fde214d2?action=test" />           <Link Rel="Undo" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/3f56fa52-c902-4655-9774-2025fde214d2?action=undo" />           <Link Rel="Delete" Type="CloudFailoverPlanReference" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/3f56fa52-c902-4655-9774-2025fde214d2" Name="ABC Company Failover Plan" />         </Links>         <TenantUid>urn:veeam:CloudTenant:e38a8692-6816-443e-9052-7fa71ee7fd65</TenantUid>         <TenantName>ABC Company</TenantName>         <Description>Cloud failover plan for ABC Company full site failover</Description>         <CloudFailoverPlanOptions>           <PostFailoverPlanCommandEnabled>false</PostFailoverPlanCommandEnabled>           <PostFailoverPlanCommand />           <PreFailoverPlanCommandEnabled>false</PreFailoverPlanCommandEnabled>           <PreFailoverPlanCommand />         </CloudFailoverPlanOptions>         <CloudFailoverPlanInfo>           <Includes>             <CloudFailoveredVm Type="CloudFailoveredVm" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/3f56fa52-c902-4655-9774-2025fde214d2/includes/a4f16718-574c-40d1-8002-30e3b72581d6">               <FailoverPlanVMId>a4f16718-574c-40d1-8002-30e3b72581d6</FailoverPlanVMId>               <Name>filesrv03</Name>               <Order>0</Order>             </CloudFailoveredVm>             <CloudFailoveredVm Type="CloudFailoveredVm" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/3f56fa52-c902-4655-9774-2025fde214d2/includes/2eb6ccd9-d41e-4cdb-8eb2-85add9479cf6">               <FailoverPlanVMId>2eb6ccd9-d41e-4cdb-8eb2-85add9479cf6</FailoverPlanVMId>               <Name>filesrv04</Name>               <Order>1</Order>             </CloudFailoveredVm>           </Includes>         </CloudFailoverPlanInfo>       </CloudFailoverPlan>     </CloudFailoverPlans>   </Entities>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=CloudFailoverPlan&format=Entities&sortAsc=Name&filter=BackupServerName=="172.24.31.67";CloudTenantName=="ABC+Company"&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=CloudFailoverPlan&format=Entities&sortAsc=Name&filter=BackupServerName=="172.24.31.67";CloudTenantName=="ABC+Company"&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

