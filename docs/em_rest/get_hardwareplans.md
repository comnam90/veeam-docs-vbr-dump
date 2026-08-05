---
title: "GET /cloud/hardwarePlans"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_hardwareplans.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cloud/hardwarePlans


Returns a resource representation of a collection of hardware plans configured on all backup servers connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of hardware plans, send the [GET /query?type=CloudHardwarePlan](get_query_cloudhardwareplan.md) request. |

Request

To get a list of hardware plans, send the GET HTTP request to the /cloud/hardwarePlans resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud/hardwarePlans |

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

In the response body, the REST API returns a representation of the /cloud/hardwarePlans resource collection.

Example

The example below returns a list of hardware plans configured on all backup servers that are currently connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud/hardwarePlans  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="CloudHardwarePlanReference" Href="https://localhost:9398/api/cloud/hardwarePlans/127e652e-e02e-4951-99e7-03280edfe536" Name="Hyper-V Silver" UID="urn:veeam:CloudHardwarePlan:127e652e-e02e-4951-99e7-03280edfe536">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudHardwarePlan" Href="https://localhost:9398/api/cloud/hardwarePlans/127e652e-e02e-4951-99e7-03280edfe536?format=Entity" Name="Hyper-V Silver" />     </Links>   </Ref>   <Ref Type="CloudHardwarePlanReference" Href="https://localhost:9398/api/cloud/hardwarePlans/ed6ad5f1-671b-4875-9d81-72a431953aca" Name="VMware Bronze" UID="urn:veeam:CloudHardwarePlan:ed6ad5f1-671b-4875-9d81-72a431953aca">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudHardwarePlan" Href="https://localhost:9398/api/cloud/hardwarePlans/ed6ad5f1-671b-4875-9d81-72a431953aca?format=Entity" Name="VMware Bronze" />     </Links>   </Ref>   <Ref Type="CloudHardwarePlanReference" Href="https://localhost:9398/api/cloud/hardwarePlans/7dc3ffa1-78a0-46a2-b098-9720c40c9915" Name="VMware Gold" UID="urn:veeam:CloudHardwarePlan:7dc3ffa1-78a0-46a2-b098-9720c40c9915">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudHardwarePlan" Href="https://localhost:9398/api/cloud/hardwarePlans/7dc3ffa1-78a0-46a2-b098-9720c40c9915?format=Entity" Name="VMware Gold" />     </Links>   </Ref>   <Ref Type="CloudHardwarePlanReference" Href="https://localhost:9398/api/cloud/hardwarePlans/d2d37ef0-dc9d-43b4-9fa4-b4e850fab171" Name="Hyper-V Gold" UID="urn:veeam:CloudHardwarePlan:d2d37ef0-dc9d-43b4-9fa4-b4e850fab171">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudHardwarePlan" Href="https://localhost:9398/api/cloud/hardwarePlans/d2d37ef0-dc9d-43b4-9fa4-b4e850fab171?format=Entity" Name="Hyper-V Gold" />     </Links>   </Ref>   <Ref Type="CloudHardwarePlanReference" Href="https://localhost:9398/api/cloud/hardwarePlans/91156f8d-8bd3-44af-bec3-b6ac2ea24288" Name="VMware Silver" UID="urn:veeam:CloudHardwarePlan:91156f8d-8bd3-44af-bec3-b6ac2ea24288">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudHardwarePlan" Href="https://localhost:9398/api/cloud/hardwarePlans/91156f8d-8bd3-44af-bec3-b6ac2ea24288?format=Entity" Name="VMware Silver" />     </Links>   </Ref>   <Ref Type="CloudHardwarePlanReference" Href="https://localhost:9398/api/cloud/hardwarePlans/82951b35-4581-4610-983a-e3a12aea1a8e" Name="Hyper-V Bronze" UID="urn:veeam:CloudHardwarePlan:82951b35-4581-4610-983a-e3a12aea1a8e">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" Name="172.17.53.48" />       <Link Rel="Alternate" Type="CloudHardwarePlan" Href="https://localhost:9398/api/cloud/hardwarePlans/82951b35-4581-4610-983a-e3a12aea1a8e?format=Entity" Name="Hyper-V Bronze" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

