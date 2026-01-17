---
title: "GET /query?type=CloudTenant"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_cloudtenant.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a collection of tenant accounts created on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/cloud/tenants](tenants.md).

Request

To get a list of tenant accounts, send the GET HTTP request to the query with the type parameter set to CloudTenant.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=CloudTenant |

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

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns a representation of the /cloud/tenants resource collection.

Example

The example below returns an entity resource representation of a collection of Active Directory tenant accounts created on the 172.24.31.67 backup server. The results are ordered in the acceding order by the Name parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=CloudTenant&format=Entities&sortAsc=name&filter=BackupServerName=="172.24.31.67";Type==ActiveDirectory    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
