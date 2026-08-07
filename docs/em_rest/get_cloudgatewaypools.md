---
title: "GET /cloud/gatewayPools"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cloudgatewaypools.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cloud/gatewayPools


Returns a resource representation of a collection of cloud gateway pools configured on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of cloud gateway pools, send the [GET /query?type=CloudGatewayPool](get_query_cloudgatewaypool.md) request. |

Request

To get a list of cloud gateway pools, send the GET HTTP request to the /cloud/gatewayPools resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/gatewayPools |

Request Headers

The request contains the following headers:

Request Headers

| Header | Required | Description |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Query Parameters

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

In the response body, the REST API returns a representation of the /cloud/gatewayPools resource collection.

Example

The example below returns a list of cloud gateway pools configured on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/gatewayPools  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Ref UID="urn:veeam:CloudGatewayPool:6de18dab-3341-441e-9184-a866913444d4" Name="Cloud gateway pool 1" Href="http://local.host:9399/api/cloud/gatewayPools/6de18dab-3341-441e-9184-a866913444d4" Type="CloudGatewayPoolReference">     <Links>       <Link Href="http://local.host:9399/api/backupServers/3e1e451a-4718-4475-836b-9547ccae6872" Name="local.host" Type="BackupServerReference" Rel="Up"/>       <Link Href="http://local.host:9399/api/cloud/gatewayPools/6de18dab-3341-441e-9184-a866913444d4?format=Entity" Name="Cloud gateway pool 1" Type="CloudGatewayPool" Rel="Alternate"/>     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

