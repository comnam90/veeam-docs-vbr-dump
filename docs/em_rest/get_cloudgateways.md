---
title: "GET /cloud/gateways"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cloudgateways.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cloud/gateways


Returns a resource representation of a collection of cloud gateways configured on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of cloud gateways, send the [GET /query?type=CloudGateway](get_query_cloudgateway.md) request. |

Request

To get a list of cloud gateways, send the GET HTTP request to the /cloud/gateways resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/gateways |

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

In the response body, the REST API returns a representation of the /cloud/gateways resource collection.

Example

The example below returns a list of cloud gateways configured on all backup servers that are currently connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/gateways  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CloudGatewayReference" Href="https://localhost:9398/api/cloud/gateways/b5025a7b-5e13-41e2-a17e-9d9af985ecfd" Name="172.16.13.97" UID="urn:veeam:CloudGateway:b5025a7b-5e13-41e2-a17e-9d9af985ecfd">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8ea5406b-a6e9-42d9-bca5-44b6a5d94af1" Name="localhost" />       <Link Rel="Alternate" Type="CloudGateway" Href="https://localhost:9398/api/cloud/gateways/b5025a7b-5e13-41e2-a17e-9d9af985ecfd?format=Entity" Name="172.16.13.97" />     </Links>   </Ref>   <Ref Type="CloudGatewayReference" Href="https://localhost:9398/api/cloud/gateways/cc79315a-2313-4360-a72a-e3b4d73f1288" Name="172.16.13.119" UID="urn:veeam:CloudGateway:cc79315a-2313-4360-a72a-e3b4d73f1288">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8ea5406b-a6e9-42d9-bca5-44b6a5d94af1" Name="localhost" />       <Link Rel="Alternate" Type="CloudGateway" Href="https://localhost:9398/api/cloud/gateways/cc79315a-2313-4360-a72a-e3b4d73f1288?format=Entity" Name="172.16.13.119" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

