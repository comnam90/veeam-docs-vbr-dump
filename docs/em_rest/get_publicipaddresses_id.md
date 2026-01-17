---
title: "GET /cloud/publicIpAddresses/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_publicipaddresses_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a public IP address that has the specified ID.

Request

To get a resource representation of the public IP address, send the GET HTTP request to the /cloud/publicIpAddresses/{ID} resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/publicIpAddresses/{ID} |

or

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/publicIpAddresses/{ID}?format=Entity |

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

In the response body, the REST API returns an entity or an entity reference of the /cloud/publicIpAddresses/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the public IP address resource, for example: urn:veeam:CloudPublicIpAddress:22d2cdad-ddd1-4789-9e27-03bf25786648. |
| Name | String | Name of the public IP address resource, for example: 198.51.100.16. |
| IpAddress | String | Public IP address, for example: 198.51.100.16. |
| TenantUid | UidType | UID of the tenant account to which the public IP address is assigned, for example: urn:veeam:CloudTenant:4f90635a-7ecc-49fe-beb6-60b37eb4bd89. |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=CloudPublicIpAddress](get_query_cloudpublicipaddress.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the pool of public IP addresses is configured. |
| /cloud/publicIpAddresses/{ID} | Alternate | Alternate URL of the [/cloud/publicIpAddresses/{ID}](publicipaddresses_id.md) resource. |
| /cloud/hardwarePlans/{ID} | Edit | URL for the [PUT /cloud/publicIpAddresses/{ID}](put_publicipaddresses_id.md) request. |
| /cloud/hardwarePlans/{ID} | Delete | URL for the [DELETE /cloud/publicIpAddresses/{ID}](delete_publicipaddresses_id.md) request. |

Example

The example below returns an entity representation of the public IP address resource that has ID 22d2cdad-ddd1-4789-9e27-03bf25786648.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/publicIpAddresses/22d2cdad-ddd1-4789-9e27-03bf25786648    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <CloudPublicIpAddress xmlns="http://www.veeam.com/ent/v1.0" Type="CloudPublicIpAddress" Href="https://localhost:9398/api/cloud/publicIpAddresses/22d2cdad-ddd1-4789-9e27-03bf25786648?format=Entity" Name="198.51.100.16" UID="urn:veeam:CloudPublicIpAddress:22d2cdad-ddd1-4789-9e27-03bf25786648" BackupServerUid="urn:veeam:BackupServer:8fff3b8e-c3f1-4ef5-aecc-561f07bf9982"> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
