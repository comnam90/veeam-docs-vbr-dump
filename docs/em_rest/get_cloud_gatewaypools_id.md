---
title: "GET /cloud/gatewayPools/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cloud_gatewaypools_id.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cloud/gatewayPools/{ID}


Returns a resource representation of a cloud gateway pool with the specified ID.

Request

To get a resource representation of the cloud gateway pool, send the GET HTTP request to the /cloud/gatewayPools/{ID} resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/gatewayPools/{ID} |

or

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/gatewayPools/{ID}?format=Entity |

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

In the response body, the REST API returns an entity or an entity reference of the /cloud/gatewayPools/{ID} resource. The resource entity contains the following parameters and links.

Parameters

Response Body

| Element | Type | Description |
| UID | UidType | UID of the cloud gateway pool resource, for example: urn:veeam:CloudGatewayPool:18b395e2-81ff-439c-ae8c-188d97274c15. |
| Name | String | Name of the cloud gateway pool resource, for example: TechCompany Gateway Pool. |
| Description | String | Description of the cloud gateway pool. |
| CloudGateways | CloudGatewayPoolGatewayListType | Specifies the list of the cloud gateways included in the cloud gateway pool. At least one cloud gateway must be specified to create a cloud gateway pool. For details, see [Cloud Gateway Settings](#cloudgateways). |
| CloudTenants | CloudGatewayPoolTenantListType | Specifies a list of cloud tenants to whom the cloud gateway pool will be assigned. This parameter is optional, because a gateway pool can be assigned to no tenants. For details, see [Cloud Tenant Settings](#cloudtenant). |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=CloudGatewayPool](get_query_cloudgatewaypool.md).

Cloud Gateway Settings

The CloudGateways element contains the following cloud gateway settings.

Response Body

| Element | Type | Description |
| CloudGatewayUid | UidType | UID of the cloud gateway included in the cloud gateway pool. Can be obtained from the representation of the [/cloud/gateways](cloudgateways.md) resource. |

Cloud Tenant Settings

The CloudTenants element contains the following cloud tenant settings.

Response Body

| Element | Type | Description |
| CloudTenantUid | UidType | UID of the tenant account to which the cloud gateway pool will be assigned. Can be obtained from the representation of the [/cloud/tenants](tenants.md) resource. |

Links

Response Body

| Reference | Relationship | Description |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the cloud gateway pool was created. |
| /cloud/gatewayPools/{ID} | Alternate | Alternate URL of the [/cloud/gatewayPools/{ID}](cloud_gatewaypools_id.md) resource. |
| /cloud/gatewayPools/{ID} | Edit | URL for the [PUT /cloud/gatewayPools/{ID}](put_cloud_gatewaypools_id.md) request. |
| /cloud/gateways/{ID} | Delete | URL for the [DELETE /cloud/gatewayPools/{ID}](delete_cloud_gatewaypools_id.md) request. |
| /cloud/gatewayPools/{ID}/gateways | Down | URL of the [/cloud/gateways](cloudgateways.md) resource — a collection of cloud gateways contained in the gateway pool. |
| /cloud/gatewayPools/{ID}/tenants | Related | URL of the [/cloud/tenants](tenants.md) resource — a collection of tenant accounts have access to the gateway pool. |

Example

The example below returns an entity reference representation of the cloud gateway pool with ID 77e85a22-aa23-4c86-bbb2-a4e55860b0ee.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/gatewayPools/77e85a22-aa23-4c86-bbb2-a4e55860b0ee?format=Entity  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <?xml version="1.0" encoding="utf-8"?> <CloudGatewayPool xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" Href="https://enterprise06.tech.local:9398/api/cloud/gatewayPools/77e85a22-aa23-4c86-bbb2-a4e55860b0ee?format=Entity" Type="CloudGatewayPool" Name="Cloud gateway pool 1" UID="urn:veeam:CloudGatewayPool:77e85a22-aa23-4c86-bbb2-a4e55860b0ee" xmlns="http://www.veeam.com/ent/v1.0">     <Links>         <Link Href="https://enterprise06.tech.local:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" Type="BackupServerReference" Rel="Up" />         <Link Href="https://enterprise06.tech.local:9398/api/cloud/gatewayPools/77e85a22-aa23-4c86-bbb2-a4e55860b0ee" Name="Cloud gateway pool 1" Type="CloudGatewayPoolReference" Rel="Alternate" />         <Link Href="https://enterprise06.tech.local:9398/api/cloud/gatewayPools/77e85a22-aa23-4c86-bbb2-a4e55860b0ee" Name="Cloud gateway pool 1" Type="CloudGatewayPoolReference" Rel="Edit" />         <Link Href="https://enterprise06.tech.local:9398/api/cloud/gatewayPools/77e85a22-aa23-4c86-bbb2-a4e55860b0ee" Rel="Delete" />         <Link Href="https://enterprise06.tech.local:9398/api/cloud/gatewayPools/77e85a22-aa23-4c86-bbb2-a4e55860b0ee/gateways" Type="CloudGatewayReferenceList" Rel="Down" />         <Link Href="https://enterprise06.tech.local:9398/api/cloud/gatewayPools/77e85a22-aa23-4c86-bbb2-a4e55860b0ee/tenants" Type="CloudTenantReferenceList" Rel="Related" />     </Links>     <Description>Created by TECH\sheila.d.cory</Description>     <CloudGateways>         <CloudGatewayUid>urn:veeam:CloudGateway:72165f41-2374-44b6-a9ac-c18a461e03fe</CloudGatewayUid>     </CloudGateways>     <CloudTenants>         <CloudTenantUid>urn:veeam:CloudTenant:91cc2590-0de3-4e9d-bd4f-048d113eadb0</CloudTenantUid>         <CloudTenantUid>urn:veeam:CloudTenant:d1a65661-b72c-4698-9232-dcb4d8de0a94</CloudTenantUid>         <CloudTenantUid>urn:veeam:CloudTenant:ca354a3d-41ff-4e2c-9d7c-f6f9cbbbf5cd</CloudTenantUid>     </CloudTenants> </CloudGatewayPool> |

Page updated 2026-07-29

