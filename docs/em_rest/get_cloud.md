---
title: "GET /cloud"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_cloud.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /cloud


Returns a set of links to Veeam Cloud Connect resources.

Request

To get a list of Veeam Cloud Connect resources, send the GET HTTP request to the /cloud resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/cloud |

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

In the response body, the REST API returns a representation of the /cloud resource.

Example

The example below returns a resource representation of the /cloud resource.

|  |
| --- |
| Request:  GET https://localhost:9398/api/cloud  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <CloudConnectService Href="http://local.host:9399/api/cloud" Type="CloudConnectService" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Links>     <Link Href="http://local.host:9399/api/logonSessions/b30eccda-7cc4-414e-b407-dab96abb6e1d" Type="LogonSession" Rel="Up"/>     <Link Href="http://local.host:9399/api/cloud/gateways" Type="CloudGatewayReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/tenants" Type="CloudTenantReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/hardwarePlans" Type="CloudHardwarePlanReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/publicIpAddresses" Type="CloudPublicIpAddressReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/cloudFailoverPlans" Type="CloudFailoverPlanReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/vmReplicaPoints" Type="CloudVmReplicaPointReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/replicas" Type="CloudReplicaReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/vlans" Type="VlanConfigurationReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/failoverSessions" Type="CloudFailoverSessionReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/gatewayPools" Type="CloudGatewayPoolReferenceList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/gateways?format=Entity" Type="CloudGatewayList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/tenants?format=Entity" Type="CloudTenantList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/hardwarePlans?format=Entity" Type="CloudHardwarePlanList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/publicIpAddresses?format=Entity" Type="CloudPublicIpAddressList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/cloudFailoverPlans?format=Entity" Type="CloudFailoverPlanList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/vmReplicaPoints?format=Entity" Type="CloudVmReplicaPointList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/replicas?format=Entity" Type="CloudReplicaList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/vlans?format=Entity" Type="VlanConfigurationList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/failoverSessions?format=Entity" Type="CloudFailoverSessionList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/gatewayPools?format=Entity" Type="CloudGatewayPoolList" Rel="Down"/>     <Link Href="http://local.host:9399/api/cloud/gateways" Rel="Create"/>     <Link Href="http://local.host:9399/api/cloud/tenants" Rel="Create"/>     <Link Href="http://local.host:9399/api/cloud/hardwarePlans" Rel="Create"/>     <Link Href="http://local.host:9399/api/cloud/publicIpAddresses" Rel="Create"/>     <Link Href="http://local.host:9399/api/cloud/gatewayPools" Rel="Create"/>   </Links> </CloudConnectService> |

Page updated 2026-07-29

