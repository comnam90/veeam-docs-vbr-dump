---
title: "GET /cloud/cloudFailoverPlans"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cloudfailoverplans.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cloud/cloudFailoverPlans


Returns a resource representation of a collection of all cloud failover plans configured by tenants on backup servers that are connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of failover plans, send the [GET /query?type=CloudFailoverPlan](get_query_cloudfailoverplan.md) request. |

Request

To get a list of cloud failover plans configured by tenants on backup servers, send the GET HTTP request to the /cloud/cloudFailoverPlans resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/cloudFailoverPlans |

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

In the response body, the REST API returns a representation of the /cloud/cloudFailoverPlans resource collection.

Example

The example below returns a list of all cloud failover plans configured by tenants on backup servers managed by Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/cloudFailoverPlans  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="FailoverPlanReference" Href="https://localhost:9398/api/managedServers/e7ca6822-a87f-443d-8aae-8005970543bf" Name="ABC Company Failover Plan" UID="urn:veeam:FailoverPlan:e7ca6822-a87f-443d-8aae-8005970543bf">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudFailoverPlan" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/e7ca6822-a87f-443d-8aae-8005970543bf?format=Entity" Name="ABC Company Failover Plan" />       <Link Rel="Related" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/b25f5f1d-a3c3-45ed-af23-9ef31a94dac7?format=Entity" Name="ABC Company" />     </Links>   </Ref>   <Ref Type="FailoverPlanReference" Href="https://localhost:9398/api/managedServers/08d5bbf5-619b-4bb9-ba51-95f4678544f4" Name="UCM Company Full SIte Failover" UID="urn:veeam:FailoverPlan:08d5bbf5-619b-4bb9-ba51-95f4678544f4">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudFailoverPlan" Href="https://localhost:9398/api/cloud/cloudFailoverPlans/08d5bbf5-619b-4bb9-ba51-95f4678544f4?format=Entity" Name="UCM Company Full SIte Failover" />       <Link Rel="Related" Type="CloudTenant" Href="https://localhost:9398/api/cloud/tenants/4e507777-8349-4683-9336-5fd1ecc27ea6?format=Entity" Name="UCM Company" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

