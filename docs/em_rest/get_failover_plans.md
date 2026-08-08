---
title: "GET /failoverPlans"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_failover_plans.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /failoverPlans


Returns a resource representation of a collection of all failover plans configured on backup servers that are connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of failover plans, send the [GET /query?type=FailoverPlan](get_query_failoverplan.md) request. |

Request

To get a list of failover plans configured on backup servers, send the GET HTTP request to the /failoverPlans resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/failoverPlans |

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

In the response body, the REST API returns a representation of the /failoverPlans resource collection.

Example

The example below returns a list of all failover plans configured on backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/failoverPlans  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="FailoverPlanReference" Href="https://localhost:9398/api/failoverPlans/ae01e36f-32a3-4095-95fa-09a2af744009" Name="SQL Failover Plan" UID="urn:veeam:FailoverPlan:ae01e36f-32a3-4095-95fa-09a2af744009">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="FailoverPlan" Href="https://localhost:9398/api/failoverPlans/ae01e36f-32a3-4095-95fa-09a2af744009?format=Entity" Name="SQL Failover Plan" />     </Links>   </Ref>   <Ref Type="FailoverPlanReference" Href="https://localhost:9398/api/failoverPlans/8c6ac2a1-8330-400e-9194-40310b5ca58a" Name="Exchange Group Failover Plan" UID="urn:veeam:FailoverPlan:8c6ac2a1-8330-400e-9194-40310b5ca58a">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/ce15a8c7-aa49-495e-b05b-ee3398c91018" Name="srv02.tech.local" />       <Link Rel="Alternate" Type="FailoverPlan" Href="https://localhost:9398/api/failoverPlans/8c6ac2a1-8330-400e-9194-40310b5ca58a?format=Entity" Name="Exchange Group Failover Plan" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

