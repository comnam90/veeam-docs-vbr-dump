---
title: "get_tenants_id_resources_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_tenants_id_resources_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource of a storage quota assigned to the tenant account with the specified ID.

Request

To get a storage quota, send the GET HTTP request to the /cloud/tenants/{ID}/resources/{ID} resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}/resources/{ID} |

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

In the response body, the REST API returns a representation of the /cloud/tenants/{ID}/resources/{ID} resource that contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| RepositoryQuota | CloudTenantRepositoryQuotaInfoType | Repository quota assigned to the tenant. For details, see [Repository Quota](#RepositoryQuota). |
| Id | String | ID of the storage quota, for example: b5025a7b-5e13-41e2-a17e-9d9af985ecfd |

Repository Quota

| Element | Type | Description |
| --- | --- | --- |
| DisplayName | String | Friendly name of the cloud repository. |
| RepositoryUid | UidType | UID of the backup repository on which the storage quota is created, for example: urn:veeam:Repository:82db96c3-445c-4a7e-9587-f2d523e839f4 |
| WanAcceleratorUid | UidType | UID of the WAN accelerator used as a target WAN accelerator with the cloud repository quota. |
| QuotaMb | Long | Size of the storage quota assigned to the tenant (in MB). |
| UsedQuota | Long | Size of the storage quota used by the tenant (in MB). |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /cloud/tenants/{ID}/resources | Delete | URL for the [DELETE /cloud/tenants/{ID}/resources/{ID}](delete_tenants_id_resources_id.md) request. |
| /cloud/tenants/{ID} | Up | URL of the [/cloud/tenants/{ID}](tenants_id.md) resource — a tenant that uses the cloud repository. |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server of the service provider. |

Example

The example below returns a storage quota having ID 1c7c6cd7-0cd0-4e20-8d15-a94d23299a93.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/tenants/2ff85684-64ae-4db8-a5f3-373a2270c1cd/resources/1c7c6cd7-0cd0-4e20-8d15-a94d23299a93    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <CloudTenantResource xmlns="http://www.veeam.com/ent/v1.0" Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/4f90635a-7ecc-49fe-beb6-60b37eb4bd89/resources/1c7c6cd7-0cd0-4e20-8d15-a94d23299a93" Id="1c7c6cd7-0cd0-4e20-8d15-a94d23299a93"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
