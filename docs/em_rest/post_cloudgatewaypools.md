---
title: "POST /cloud/gatewayPools"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_cloudgatewaypools.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# POST /cloud/gatewayPools


Configures a new cloud gateway pool on the backup server connected to Veeam Backup Enterprise Manager.

To configure a cloud gateway pool, you must have at least one cloud gateway configured on the backup server.

Request

To create a new cloud gateway pool, send the POST HTTP request to the /cloud/gatewayPools resource.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/cloud/gatewayPools |

Request Header

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters for the new cloud gateway pool. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Name | String | Name of the created cloud gateway pool. | Yes | 1/1 |
| Description | String | Description for the created cloud gateway pool. | Yes | 0/1 |
| CloudGateways | CloudGatewayPool | Specifies the list of cloud gateways included in the cloud gateway pool. At least one cloud gateway must be specified to create a cloud gateway pool. For details, see [Cloud Gateway Settings](#cloudgateways). | Yes | 1/1 |
| CloudTenants | CloudGatewayPool | Specifies the list of cloud tenants to whom the created cloud gateway pool will be assigned. This parameter is optional, because a cloud gateway pool can be assigned to no tenants. For details, see [Cloud Tenant Settings](#cloudtenant). | Yes | 0/1 |
| BackupServerUid | UidType | UID of the backup server on which the cloud gateway pool must be created. | Yes | 1/1 |

For example:

XML Representation

|  |
| --- |
| <CreateCloudGatewayPoolSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Name>GatewayPool 1</Name>   <Description>Created by REST API</Description>   <CloudGateways>     <CloudGatewayUid>urn:veeam:CloudGateway:0eade4fd-0b0c-4ce4-8c1f-ca60ec682d0e</CloudGatewayUid>   </CloudGateways>   <CloudTenants>     <CloudTenantUid>urn:veeam:CloudTenant:5cf540af-512a-5ba8-9f12-77fba51207e0</CloudTenantUid>   </CloudTenants>   <BackupServerUid>urn:veeam:BackupServer:8c88c6d6-931f-4044-8c0b-7a0c5f188b00 179011f9-62c3-498c-9b5a-d5f227fd1dce</BackupServerUid> </CreateCloudGatewayPoolSpec> |

JSON Representation

|  |
| --- |
| {   "Name": "GatewayPool 1",   "Description": "Created by REST API",   "CloudGateways": {     "CloudGatewayUids": [       "urn:veeam:CloudGateway:0eade4fd-0b0c-4ce4-8c1f-ca60ec682d0e"     ]   },   "CloudTenants": {     "CloudTenantUids": [       "urn:veeam:CloudTenant:5cf540af-512a-5ba8-9f12-77fba51207e0"     ]   },   "BackupServerUid": "urn:veeam:BackupServer:8c88c6d6-931f-4044-8c0b-7a0c5f188b00 179011f9-62c3-498c-9b5a-d5f227fd1dce"  } |

Cloud Gateway Settings

You can define the following parameters:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| CloudGatewayUid | UidType | UID of the cloud gateway included in the created cloud gateway pool. Can be obtained from the representation of the [/cloud/gateways](cloudgateways.md) resource. | Yes | 1/Unbounded |

For example:

XML Representation

|  |
| --- |
| <CloudGateways>   <CloudGatewayUid>urn:veeam:CloudGateway:0eade4fd-0b0c-4ce4-8c1f-ca60ec682d0e</CloudGatewayUid> </CloudGateways> |

JSON Representation

|  |
| --- |
| "CloudGateways": {   "CloudGatewayUids": [     "urn:veeam:CloudGateway:0eade4fd-0b0c-4ce4-8c1f-ca60ec682d0e"   ]  } |

Cloud Tenant Settings

You can define the following parameters:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| CloudTenantUid | UidType | UID of the tenant account to which the created cloud gateway pool will be assigned. Can be obtained from the representation of the [/cloud/tenants](tenants.md) resource. | Yes | 1/Unbounded |

For example:

XML Representation

|  |
| --- |
| <CloudTenants>   <CloudTenantUid>urn:veeam:CloudTenant:5cf540af-512a-5ba8-9f12-77fba51207e0</CloudTenantUid> </CloudTenants> |

JSON Representation

|  |
| --- |
| "CloudTenants": {   "CloudTenantUids": [     "urn:veeam:CloudTenant:5cf540af-512a-5ba8-9f12-77fba51207e0"   ]  } |

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 202 Accepted.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

None.

Example

The example below creates a cloud gateway pool on the backup server having UID urn:veeam:BackupServer:29e5d158-1f58-44bc-bbaa-2752d787a91d.

|  |
| --- |
| Request:  POST https://localhost:9398/api/cloud/gatewayPools    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <CreateCloudGatewayPoolSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Name>GatewayPool 1</Name>   <Description>Created by REST API</Description>   <CloudGateways>     <CloudGatewayUid>urn:veeam:CloudGateway:3e4e6d17-ee2a-430f-807c-8d92af2a5551</CloudGatewayUid>   </CloudGateways>   <CloudTenants>     <CloudTenantUid>urn:veeam:CloudTenant:5cf540af-512a-5ba8-9f12-77fba51207e0</CloudTenantUid>   </CloudTenants>   <BackupServerUid>urn:veeam:BackupServer:29e5d158-1f58-44bc-bbaa-2752d787a91d</BackupServerUid> </CreateCloudGatewayPoolSpec>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>CreateCloudGatewayPool</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />     <Link Rel="Related" Type="CloudGatewayPools" Href="https://localhost:9398/api/cloud/gatewayPools/64bf55fb-b53f-4214-950a-fcc3a241622b?format=Entity" Name="" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>CreateCloudGatewayPool</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |


