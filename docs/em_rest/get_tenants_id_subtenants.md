---
title: "GET /cloud/tenants/{ID}/subtenants"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_tenants_id_subtenants.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cloud/tenants/{ID}/subtenants


Returns a list of subtenant accounts created for the tenant account with the specified ID.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of subtenants accounts, send the [GET /query?type=CloudSubtenant](get_query_cloudsubtenant.md) request. |

Request

To get a list of subtenant accounts, send the GET HTTP request to the /cloud/tenants/{ID}/subtenants resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}/subtenants |

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

In the response body, the REST API returns a representation of the /cloud/tenants/{ID}/subtenants resource.

Example

The example below returns a list of subtenant accounts created for the tenant account with ID 28ddf9b9-12fa-431a-a34c-a327f05c3920.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/tenants/28ddf9b9-12fa-431a-a34c-a327f05c3920/subtenants  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <CloudSubtenants xmlns="http://www.veeam.com/ent/v1.0">   <CloudSubtenant Type="CloudSubtenant" Href="https://localhost:9398/api/cloud/tenants/28ddf9b9-12fa-431a-a34c-a327f05c3920/subtenants/0eb0c130-d91a-4e05-9403-ac2ded0fc1ea" Id="0eb0c130-d91a-4e05-9403-ac2ded0fc1ea">     <Links>       <Link Rel="Edit" Type="CloudSubtenant" Href="https://localhost:9398/api/cloud/tenants/28ddf9b9-12fa-431a-a34c-a327f05c3920/subtenants/0eb0c130-d91a-4e05-9403-ac2ded0fc1ea" Name="ABC Company User 01" />       <Link Rel="Delete" Href="https://localhost:9398/api/cloud/tenants/28ddf9b9-12fa-431a-a34c-a327f05c3920/subtenants/0eb0c130-d91a-4e05-9403-ac2ded0fc1ea" />       <Link Rel="Up" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/28ddf9b9-12fa-431a-a34c-a327f05c3920?format=Entity" Name="ABC Company" />       <Link Rel="Up" Type="BackupServer" Href="https://localhost:9398/api/backupServers/1cf4ea89-89d9-4b4e-a285-71bd8c705222?format=Entity" Name="172.17.53.2" />     </Links>     <Name>ABC Company User 01</Name>     <Description>ABC Company PC User</Description>     <Password />     <Enabled>true</Enabled>     <RepositoryQuota Unlimited="true">       <DisplayName>Cloud Vol User 01</DisplayName>       <TenantResourceId>11c59670-23df-448c-a4b3-74c42669633e</TenantResourceId>       <QuotaMb>1024</QuotaMb>       <UsedQuotaMb>0</UsedQuotaMb>     </RepositoryQuota>   </CloudSubtenant>   <CloudSubtenant Type="CloudSubtenant" Href="https://localhost:9398/api/cloud/tenants/28ddf9b9-12fa-431a-a34c-a327f05c3920/subtenants/9cf1953a-0bf5-4eb4-982c-fac1945eef4f" Id="9cf1953a-0bf5-4eb4-982c-fac1945eef4f">     <Links>       <Link Rel="Edit" Type="CloudSubtenant" Href="https://localhost:9398/api/cloud/tenants/28ddf9b9-12fa-431a-a34c-a327f05c3920/subtenants/9cf1953a-0bf5-4eb4-982c-fac1945eef4f" Name="ABC Company User 02" />       <Link Rel="Delete" Href="https://localhost:9398/api/cloud/tenants/28ddf9b9-12fa-431a-a34c-a327f05c3920/subtenants/9cf1953a-0bf5-4eb4-982c-fac1945eef4f" />       <Link Rel="Up" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/28ddf9b9-12fa-431a-a34c-a327f05c3920?format=Entity" Name="ABC Company" />       <Link Rel="Up" Type="BackupServer" Href="https://localhost:9398/api/backupServers/1cf4ea89-89d9-4b4e-a285-71bd8c705222?format=Entity" Name="172.17.53.2" />     </Links>     <Name>ABC Company User 02</Name>     <Description>ABC Company Laptop User</Description>     <Password />     <Enabled>true</Enabled>     <RepositoryQuota Unlimited="true">       <DisplayName>Cloud Vol User 02</DisplayName>       <TenantResourceId>11c59670-23df-448c-a4b3-74c42669633e</TenantResourceId>       <QuotaMb>10240</QuotaMb>       <UsedQuotaMb>0</UsedQuotaMb>     </RepositoryQuota>   </CloudSubtenant> </CloudSubtenants> |

Page updated 2026-07-29

