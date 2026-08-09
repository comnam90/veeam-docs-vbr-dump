---
title: "GET /selfService/vSphere/Configs"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_selfservice_vsphere_configs.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /selfService/vSphere/Configs


Returns a resource representation of a collection of vSphere Self-Service Backup Portal tenant access configurations.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of tenant access configurations, send the [GET /query?type=VsphereSelfServiceConfig](get_query_vsphereselfserviceconfig.md) request. |

Request

To get a list of vSphere Self-Service Backup Portal tenant access configurations, send the GET HTTP request to the /selfService/vSphere/Configs resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/selfService/vSphere/Configs |

Request Header

The request contains the following headers:

Request Header

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

In the response body, the REST API returns a representation of the /selfService/vSphere/Configs resource.

Example

The example below returns a list of vSphere Self-Service Backup Portal tenant access configurations.

|  |
| --- |
| Request:  GET https://localhost:9398/api/selfService/vSphere/Configs  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0">   <Ref Type="VSphereSelfServiceConfigReference" Href="https://localhost:9398/api/selfService/vSphere/Configs/4d1af399-b55d-444a-acd6-961f889edf09" Name="William Fox" UID="urn:veeam:VSphereSelfServiceConfig:4d1af399-b55d-444a-acd6-961f889edf09">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />       <Link Rel="Alternate" Type="VSphereSelfServiceConfig" Href="https://localhost:9398/api/selfService/vSphere/Configs/4d1af399-b55d-444a-acd6-961f889edf09?format=Entity" Name="William Fox" />     </Links>   </Ref>   <Ref Type="VSphereSelfServiceConfigReference" Href="https://localhost:9398/api/selfService/vSphere/Configs/c6a041d0-36a1-47c7-9f4b-a12327796c68" Name="Administrators" UID="urn:veeam:VSphereSelfServiceConfig:c6a041d0-36a1-47c7-9f4b-a12327796c68">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />       <Link Rel="Alternate" Type="VSphereSelfServiceConfig" Href="https://localhost:9398/api/selfService/vSphere/Configs/c6a041d0-36a1-47c7-9f4b-a12327796c68?format=Entity" Name="Administrators" />     </Links>   </Ref>   <Ref Type="VSphereSelfServiceConfigReference" Href="https://localhost:9398/api/selfService/vSphere/Configs/a6ca480a-e7eb-4524-939e-bba8c7587d0e" Name="Domain Users" UID="urn:veeam:VSphereSelfServiceConfig:a6ca480a-e7eb-4524-939e-bba8c7587d0e">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />       <Link Rel="Alternate" Type="VSphereSelfServiceConfig" Href="https://localhost:9398/api/selfService/vSphere/Configs/a6ca480a-e7eb-4524-939e-bba8c7587d0e?format=Entity" Name="Domain Users" />     </Links>   </Ref> </EntityReferences> |

Page updated 2026-07-29

