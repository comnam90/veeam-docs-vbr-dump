---
title: "GET /cloud/tenants/{ID}/resources"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_tenants_id_resources.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cloud/tenants/{ID}/resources


Returns a collection of storage quotas assigned to the tenant account with the specified ID.

Request

To get a list of tenant account storage quotas, send the GET HTTP request to the /cloud/tenants/{ID}/resources resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}/resources |

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

In the response body, the REST API returns a representation of the /cloud/tenants/{ID}/resources resource.

Example

The example below returns storage quotas for the tenant account with ID 4f90635a-7ecc-49fe-beb6-60b37eb4bd89.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89/resources  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <CloudTenantResources xmlns="http://www.veeam.com/ent/v1.0">   <CloudTenantResource Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89/resources/7401a50c-4dba-4fc9-81a8-2b33afdb2e39" Id="7401a50c-4dba-4fc9-81a8-2b33afdb2e39">     <Links>       <Link Rel="Delete" Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89/resources/7401a50c-4dba-4fc9-81a8-2b33afdb2e39" Name="Cloud repository 2" />       <Link Rel="Up" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89?format=Entity" Name="ABC Company" />       <Link Rel="Up" Type="BackupServer" Href="https://localhost:9398/api/backupServers/8ea5406b-a6e9-42d9-bca5-44b6a5d94af1?format=Entity" Name="localhost" />     </Links>     <RepositoryQuota>       <DisplayName>Cloud repository 2</DisplayName>       <RepositoryUid>urn:veeam:Repository:bcf56d1e-acc8-4099-8708-00f62930b1ac</RepositoryUid>       <Quota>10240</Quota>       <UsedQuota>0</UsedQuota>     </RepositoryQuota>   </CloudTenantResource>   <CloudTenantResource Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89/resources/725fad57-2606-4903-98ba-b435f303670e" Id="725fad57-2606-4903-98ba-b435f303670e">     <Links>       <Link Rel="Delete" Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89/resources/725fad57-2606-4903-98ba-b435f303670e" Name="Cloud repository 1" />       <Link Rel="Up" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89?format=Entity" Name="ABC Company" />       <Link Rel="Up" Type="BackupServer" Href="https://localhost:9398/api/backupServers/8ea5406b-a6e9-42d9-bca5-44b6a5d94af1?format=Entity" Name="localhost" />     </Links>     <RepositoryQuota>       <DisplayName>Cloud repository 1</DisplayName>       <RepositoryUid>urn:veeam:Repository:82db96c3-445c-4a7e-9587-f2d523e839f4</RepositoryUid>       <Quota>10240</Quota>       <UsedQuota>0</UsedQuota>     </RepositoryQuota>   </CloudTenantResource> </CloudTenantResources> |

Page updated 2026-07-29

