---
title: "GET /cloud/tenants/{ID}/subtenants/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_tenants_id_subtenants_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of the subtenat account with the specified ID created for the tenant account with the specified ID.

Request

To get a resource representation of the subtenant account, send the GET HTTP request to the /cloud/tenants/{ID}/subtenants/{ID} resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}/subtenants/{ID} |

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

In the response body, the REST API returns an entity or an entity reference of the /cloud/tenants/{ID}/subtenants/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| Id | String | ID of the subtenant account resource, for example: 4da30260-581d-4b94-8a56-61c117819dcc. |
| Name | String | Name of the subtenant account, for example: ABC Company PC User. |
| Description | String | Description for the subtenant account. |
| Password | String | Password for the subtenant account. |
| Enabled | Boolean | Defines whether the subtenant account is in the disabled or enabled state. Possible values:   * True — the subtenant account is enabled * False — the subtenant account is disabled |
| RepositoryQuota | CloudSubtenantRepositoryQuotaInfoType | Parameters for the storage quota assigned to the subtenant account. For details, see [Subtenant Quota Settings](#subquota). |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=CloudSubtenant](get_query_cloudsubtenant.md).

Subtenant Quota Settings

The RepositoryQuota element contains the following subtenant quota settings.

| Element | Type | Description |
| --- | --- | --- |
| DisplayName | String | Friendly name of the storage quota assigned to the subtenant. |
| TenantResourceId | String | ID of the tenant storage quota on which the storage quota for the subtenant account must be created, for example: 11c59670-23df-448c-a4b3-74c42669633e. |
| QuotaMb | Int | Size of the storage quota assigned to the subtenant (in MB). |
| UsedQuotaMb | Int | Amount of used space within the storage quota assigned to the subtenant account (in MB). |
| QuotaId | String | ID of the storage quota assigned to the subtenant, for example: 724f861d-16e7-40ee-8b68-cf7b51c31d61. |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the cloud hardware plan was created. |
| /cloud/tenants/{ID} | Up | URL of the [/cloud/tenants/{ID}](tenants_id.md) resource — a tenant that created the subtenant. |
| /cloud/tenants/{ID}/subtenants/{ID} | Edit | URL for the [PUT /cloud/tenants/{ID}/subtenants/{ID}](put_tenants_id_subtenants_id.md) request. |
| /cloud/tenants/{ID}/subtenants/{ID} | Delete | URL for the [DELETE /cloud/tenants/{ID}/subtenants/{ID}](delete_tenants_id_subtenants_id.md) request. |

Example

The example below returns an entity representation of the subtenant account with ID 0eb0c130-d91a-4e05-9403-ac2ded0fc1ea. The subtenant account was created for the tenant account with ID 28ddf9b9-12fa-431a-a34c-a327f05c3920.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/tenants/28ddf9b9-12fa-431a-a34c-a327f05c3920/subtenants/0eb0c130-d91a-4e05-9403-ac2ded0fc1ea    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <CloudSubtenant xmlns="http://www.veeam.com/ent/v1.0" Type="CloudSubtenant" Href="https://localhost:9398/api/cloud/tenants/28ddf9b9-12fa-431a-a34c-a327f05c3920/subtenants/0eb0c130-d91a-4e05-9403-ac2ded0fc1ea" Id="0eb0c130-d91a-4e05-9403-ac2ded0fc1ea"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
