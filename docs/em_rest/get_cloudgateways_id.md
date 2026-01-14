---
title: "get_cloudgateways_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cloudgateways_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a cloud gateway having the specified ID.

Request

To get a resource representation of the cloud gateway, send the GET HTTP request to the /cloud/gateways/{ID} resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/gateways/{ID} |

or

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/gateways/{ID}?format=Entity |

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

In the response body, the REST API returns an entity or an entity reference of the /cloud/gateways/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the cloud gateway, for example: urn:veeam:CloudGateway:b5025a7b-5e13-41e2-a17e-9d9af985ecfd. |
| Name | String | DNS name or IP address (depending on what was used in POST request when creating the cloud gateway) of the the cloud gateway, for example: srv01.tech.local. |
| Enabled | Boolean | Defines if the cloud gateway is in the enabled or disabled state. Possible values:   * True * False |
| NetworkMode | CloudGatewayNetworkingMode | Network mode:   * Direct (if clients have a direct connection to the cloud gateway) * NAT (if the cloud gateway is located behind the NAT) |
| ExternalIP | String | External IP address of the NAT gateway. This parameter must be specified if the cloud gateway is located behind the NAT. |
| ExternalPort | UShort | TCP/IP port over which users' backup servers must communicate with the cloud gateway. By default, port 6180 is used. |
| InternalPort | UShort | Port on the NAT gateway used for listening to connections from users. By default, port 6180 is used. This parameter must be specified if the cloud gateway is located behind the NAT. |
| Description | String | Description for the cloud gateway. |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=CloudGateway](get_query_cloudgateway.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server where the cloud gateway was created. |
| /cloud/gateways/{ID} | Alternate | Alternate URL of the [/cloud/gateways/{ID}](cloudgateways_id.md) resource. |
| /cloud/gateways/{ID} | Edit | URL for the [PUT /cloud/gateways/{ID}](put_cloudgateways_id.md) request. |
| /cloud/gateways/{ID} | Delete | URL for the [DELETE /cloud/gateways/{ID}](delete_cloudgateways_id.md) request. |
| /cloud/gatewayPools/{ID} | Related | URL of the [/cloud/gatewayPools/{ID}](cloud_gatewaypools_id.md) resource — a cloud gateway pool that contains the gateway. |

Example

The example below returns an entity representation of the cloud gateway having ID 72165f41-2374-44b6-a9ac-c18a461e03fe.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/gateways/72165f41-2374-44b6-a9ac-c18a461e03fe?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <?xml version="1.0" encoding="utf-8"?> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
