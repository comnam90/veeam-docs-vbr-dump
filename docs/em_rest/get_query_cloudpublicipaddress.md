---
title: "get_query_cloudpublicipaddress"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_cloudpublicipaddress.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a collection of public IP addresses allocated in the service provider's network infrastructure and specified in Veeam Backup & Replication settings on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/cloud/publicIpAddresses](publicipaddresses.md).

Request

To get a list of public IP addresses, send the GET HTTP request to the query with the type parameter set to CloudPublicIpAddress.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=CloudPublicIpAddress |

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
| UID | UidType | UID of the public IP address resource, for example: urn:veeam:CloudPublicIpAddress:22d2cdad-ddd1-4789-9e27-03bf25786648. |
| Name | String | Name of the public IP address resource, for example: 198.51.100.16. |
| IpAddress | String | Public IP address, for example: 198.51.100.16. |
| CloudTenantUid | UidType | UID of the tenant account to which the public IP address is assigned, for example: urn:veeam:CloudTenant:4f90635a-7ecc-49fe-beb6-60b37eb4bd89. |
| CloudTenantName | String | Name of the tenant account to which the public IP address is assigned, for example: Cloud Tenant. |
| BackupServerUId | UidType | UID of the backup server on which the pool of public IP addresses is configured. |
| BackupServerName | String | Name of the backup server on which the pool of public IP addresses is configured. |

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

In the response body, the REST API returns a representation of the /cloud/publicIpAddresses resource collection.

Example

The example below returns an entity resource representation of a collection of IP addresses configured on the 172.24.31.67 backup server and assigned to the tenant with ID urn:veeam:CloudTenant:e38a8692-6816-443e-9052-7fa71ee7fd65. The results are ordered in the acceding order by the Name parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=CloudPublicIpAddress&format=Entities&sortAsc=Name&filter=BackupServerName=="172.24.31.67";CloudTenantUid=="urn:veeam:CloudTenant:e38a8692-6816-443e-9052-7fa71ee7fd65"      Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
