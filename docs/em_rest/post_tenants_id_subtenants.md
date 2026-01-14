---
title: "post_tenants_id_subtenants"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_tenants_id_subtenants.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Creates a subtenant account for a tenant account with the specified ID.

Request

To create a subtenant account for a tenant, send the POST HTTP request to the /cloud/tenants/{ID}/subtenants resource.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}/subtenants |

Request Header

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters of the storage quota. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Name | String | User name for the subtenant account. | Yes | 1/1 |
| Description | String | Description for the subtenant account. | Yes | 0/1 |
| Password | String | Password for the subtenant account. | Yes | 1/1 |
| Enabled | Boolean | Defines if the subtenant account must be in the enabled or disabled state. Possible values:   * True * False | Yes | 0/1 |
| TenantResourceId | String | ID of the tenant storage quota on which the storage quota for the subtenant account must be created, for example: 11c59670-23df-448c-a4b3-74c42669633e. | Yes | 1/1 |
| QuotaName | String | Friendly name of the storage quota assigned to the subtenant. | Yes | 0/1 |
| QuotaMb | Int | Size of the storage quota assigned to the subtenant (in MB). Subtenant quota cannot be less than 1GB. Size of the subtenant quota must be defined if the False value is specified in the UnlimitedQuota element. | Yes | 0/1 |
| UnlimitedQuota | Boolean | Defines if the storage quota assigned to the subtenant must be unlimited. Possible values:   * True — the subquota is not limited. The subtenant can use all storage space available within the tenant quota. The subtenant quota limit specified in the QuotaMb element is ignored. * False — the subtenant quota is limited. Size of the subtenant quota must be defined in the QuotaMb element. | Yes | 1/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "Name": "ABC Company User 02",   "Description": "ABC Company Laptop User",   "Password": "12345678",   "Enabled": true,   "TenantResourceId": "11c59670-23df-448c-a4b3-74c42669633e",   "QuotaName": "User1Quota",   "QuotaMb": 10240,   "UnlimitedQuota": true  } |

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

The example below creates a subtenant account for the tenant account with ID 28ddf9b9-12fa-431a-a34c-a327f05c3920.

|  |
| --- |
| Request:  POST https://localhost:9398/api/cloud/tenants/28ddf9b9-12fa-431a-a34c-a327f05c3920/subtenants    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <CloudSubtenantCreateSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Name>ABC Company User 02</Name>   <Description>ABC Company Laptop User</Description>   <Password>12345678</Password>   <Enabled>true</Enabled>   <TenantResourceId>11c59670-23df-448c-a4b3-74c42669633e</TenantResourceId>   <QuotaName>User1Quota</QuotaName>   <QuotaMb>10240</QuotaMb>   <UnlimitedQuota>true</UnlimitedQuota> </CloudSubtenantCreateSpec>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>AddCloudSubtenant</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>AddCloudSubtenant</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
