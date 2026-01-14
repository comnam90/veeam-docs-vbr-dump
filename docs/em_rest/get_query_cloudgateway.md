---
title: "get_query_cloudgateway"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_cloudgateway.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a collection of cloud gateways configured on backup servers connected to Veeam Backup Enterprise Manager. For details, see [/cloud/gateways](cloudgateways.md).

Request

To get a list of cloud gateways, send the GET HTTP request to the query with the type parameter set to CloudGateway.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=CloudGateway |

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
| UID | UidType | UID of the cloud gateway, for example: urn:veeam:CloudGateway:b5025a7b-5e13-41e2-a17e-9d9af985ecfd |
| Name | String | DNS name or IP address (depending on what was used in POST request when creating the cloud gateway) of the the cloud gateway, for example: srv01.tech.local. |
| Enabled | Boolean | Defines if the cloud gateway is in the enabled or disabled state. Possible values:   * True * False |
| Description | String | Description of the cloud gateway. |
| BackupServerUId | UidType | UID of the backup server parent to the cloud gateway resource. |
| BackupServerName | String | Name of the backup server parent to the cloud gateway resource. |

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

In the response body, the REST API returns a representation of the /cloud/gateways resource collection.

Example

The example below returns an entity resource representation of a collection of enabled cloud gateways configured on the 172.24.31.67 backup server. The results are ordered in the acceding order by the Name parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=CloudGateway&format=Entities&sortAsc=name&filter=BackupServerName=="172.24.31.67";Enabled==true    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
