---
title: "PUT /cloud/gatewayPools/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/put_cloud_gatewaypools_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# PUT /cloud/gatewayPools/{ID}


Edits settings of a cloud gateway pool with the specified ID.

Request

To edit settings of the cloud gateway pool, send the PUT HTTP request to the /cloud/gatewayPools/{ID} resource.

HTTP Request

|  |
| --- |
| PUT https://<Enterprise-Manager>:9398/api/cloud/gatewayPools/{ID} |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters for the cloud gateway pool which settings must be updated. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Name | String | Name of the cloud gateway pool. | Yes | 1/1 |
| Description | String | Description of the cloud gateway pool. | Yes | 0/1 |
| CloudGateways | CloudGatewayPool | Specifies the list of the cloud gateways included in the cloud gateway pool. At least one cloud gateway must be specified to create a cloud gateway pool. For details, see [Cloud Gateway Settings](#cloudgateways). | Yes | 1/1 |
| CloudTenants | CloudGatewayPool | Specifies a list of cloud tenants to whom the cloud gateway pool will be assigned. This parameter is optional, because a gateway pool can be assigned to no tenants. For details, see [Cloud Tenant Settings](#cloudtenant). | Yes | 0/1 |
| BackupServerUid | UidType | UID of the backup server on which the cloud gateway pool must be created. | Yes | 1/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> <CloudGatewayPool Href="https://localhost:9398/api/cloud/gatewayPools/dcdca4d9-f850-4094-813e-f1aa9ba8bcfb?format=Entity" Type="CloudGatewayPool" Name="Cloud gateway pool 1" UID="urn:veeam:CloudGatewayPool:dcdca4d9-f850-4094-813e-f1aa9ba8bcfb" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Description>Created by Administrator</Description>   <CloudGateways>     <CloudGatewayUid>urn:veeam:CloudGateway:d59b541c-c7e0-4179-af6d-e78eac78e893</CloudGatewayUid>   </CloudGateways>   <CloudTenants/> </CloudGatewayPool> |

JSON Representation

|  |
| --- |
| {   "Description": "Created by Administrator",   "CloudGateways": {     "CloudGatewayUids": [       "urn:veeam:CloudGateway:d59b541c-c7e0-4179-af6d-e78eac78e893"     ]   },   "CloudTenants": {},   "Name": "Cloud gateway pool 1",   "UID": "urn:veeam:CloudGatewayPool:dcdca4d9-f850-4094-813e-f1aa9ba8bcfb",   "Href": "https://localhost:9398/api/cloud/gatewayPools/dcdca4d9-f850-4094-813e-f1aa9ba8bcfb?format\u003dEntity",   "Type": "CloudGatewayPool"  } |

Cloud Gateway Settings

You can define the following parameters:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| CloudGatewayUid | UidType | UID of the cloud gateway included in the cloud gateway pool. Can be obtained from the representation of the [/cloud/gateways](cloudgateways.md) resource. | Yes | 1/Unbounded |

For example:

XML Representation

|  |
| --- |
| <CloudGateways>   <CloudGatewayUid>urn:veeam:CloudGateway:0eade4fd-0b0c-4ce4-8c1f-ca60ec682d0e</CloudGatewayUid> </CloudGateways> |

JSON Representation

|  |
| --- |
| "CloudGateways": {   "CloudGatewayUids": [     "urn:veeam:CloudGateway:d59b541c-c7e0-4179-af6d-e78eac78e893"   ]  } |

Cloud Tenant Settings

You can define the following parameters:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| CloudTenantUid | UidType | UID of the tenant account to which the cloud gateway pool will be assigned. Can be obtained from the representation of the [/cloud/tenants](tenants.md) resource. | Yes | 1/Unbounded |

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

The example below updates the description for the cloud gateway pool with ID 4f90635a-7ecc-49fe-beb6-60b37eb4bd89.

|  |
| --- |
| Request:  PUT https://localhost:9398/api/cloud/gatewayPools/4f90635a-7ecc-49fe-beb6-60b37eb4bd89    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <CloudGatewayPool Href="https://localhost:9398/api/cloud/gatewayPools/4f90635a-7ecc-49fe-beb6-60b37eb4bd89?format=Entity" Type="CloudGatewayPool" Name="Cloud gateway pool 1" UID="urn:veeam:CloudGatewayPool:dcdca4d9-f850-4094-813e-f1aa9ba8bcfb" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Description>Created by Administrator</Description>   <CloudGateways>     <CloudGatewayUid>urn:veeam:CloudGateway:d59b541c-c7e0-4179-af6d-e78eac78e893</CloudGatewayUid>   </CloudGateways>   <CloudTenants/> </CloudGatewayPool>    Response:  202 Accepted    Response Body:  <?xml version="1.0" encoding="utf-8"?> <Task xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" Href="https://localhost:9398/api/tasks/task-2" Type="Task">   <Links>     <Link Href="https://localhost:9398/api/tasks/task-2" Rel="Delete"/>   </Links>   <TaskId>task-2</TaskId>   <State>Running</State>   <Operation>UpdateCloudGatewayPool</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-2    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-2">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-2" />   </Links>   <TaskId>task-2</TaskId>   <State>Finished</State>   <Operation>UpdateCloudGatewayPool</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |


