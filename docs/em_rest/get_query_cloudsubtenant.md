---
title: "get_query_cloudsubtenant"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_cloudsubtenant.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a list of subtenant accounts created for tenant accounts. For details, see [/cloud/tenants/{ID}/subtenants](tenants_id_subtenants.md).

Request

To get a list of subtenant accounts, send the GET HTTP request to the query with the type parameter set to CloudSubtenant.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=CloudSubtenant |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Optional Parameters

In the query, you can use the following parameters for filtering and sorting.

| Parameter | Type | Description |
| --- | --- | --- |
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

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns a representation of the /cloud/tenants/{ID}/subtenants resource collection.

Example

The example below returns an entity resource representation of a collection of enabled subtenant accounts created for the ABC Company tenant on the 172.24.31.67 backup server. The results are ordered in the acceding order by the Name parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=CloudSubtenant&format=Entities&sortAsc=Name&filter=BackupServerName=="172.24.31.67";Disabled==false;CloudTenantName=="ABC Company"    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
