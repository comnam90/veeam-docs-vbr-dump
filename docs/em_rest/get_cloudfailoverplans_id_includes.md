---
title: "GET /cloud/cloudFailoverPlans/{ID}/includes"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cloudfailoverplans_id_includes.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cloud/cloudFailoverPlans/{ID}/includes


Returns a list of VMs added to the cloud failover plan that has the specified ID.

Request

To get a list of all VMs added to the cloud failover plan, send the GET HTTP request to the /cloud/cloudFailoverPlans/{ID}/includes resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/cloudFailoverPlans/{ID}/includes |

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

In the response body, the REST API returns a representation of the /cloud/cloudFailoverPlans/{ID}/includes resource collection.

Example

The example below returns a list of VMs added to the cloud failover plan that has ID e8d3df9a-70ba-492e-b39d-ab772e7defd5.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/cloudFailoverPlans/e8d3df9a-70ba-492e-b39d-ab772e7defd5/includes  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <?xml version="1.0" encoding="utf-8"?> <CloudFailoveredVms xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">     <CloudFailoveredVm Href="https://enterprise06.tech.local:9398/api/cloud/cloudFailoverPlans/e8d3df9a-70ba-492e-b39d-ab772e7defd5/includes/592cd62d-c7a2-4f19-a545-ed73ab696e42" Type="CloudFailoveredVm">         <FailoverPlanVMId>592cd62d-c7a2-4f19-a545-ed73ab696e42</FailoverPlanVMId>         <Name>apache05</Name>         <Order>0</Order>     </CloudFailoveredVm>     <CloudFailoveredVm Href="https://enterprise06.tech.local:9398/api/cloud/cloudFailoverPlans/e8d3df9a-70ba-492e-b39d-ab772e7defd5/includes/6fac81de-6012-45ff-adba-e01d28b19914" Type="CloudFailoveredVm">         <FailoverPlanVMId>6fac81de-6012-45ff-adba-e01d28b19914</FailoverPlanVMId>         <Name>enterprise04</Name>         <Order>1</Order>     </CloudFailoveredVm> </CloudFailoveredVms> |

Page updated 2026-07-29

