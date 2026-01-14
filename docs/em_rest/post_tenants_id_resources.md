---
title: "post_tenants_id_resources"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_tenants_id_resources.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Creates a storage quota on the cloud repository for a tenant account with the specified ID.

Request

To create a storage quota for a tenant account, send the POST HTTP request to the /cloud/tenants/{ID}/resources resource.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID}/resources |

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
| Name | String | Friendly name of the cloud repository. | Yes | 1/1 |
| RepositoryUid | UidType | UID of the backup repository on which the storage quota must be created, for example: urn:veeam:Repository:82db96c3-445c-4a7e-9587-f2d523e839f4 | Yes | 1/1 |
| QuotaMb | Int | Size of the storage quota assigned to the user (in MB). Storage quota cannot be less than 1GB. | Yes | 1/1 |
| WanAcceleratorUid | UidType | UID of the WAN accelerator that must be used as a target WAN accelerator with the cloud repository. This parameter must be specified if you want cloud tenants to communicate with the cloud repository through WAN accelerators. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "Name": "",   "RepositoryUid": "urn:veeam:Repository:00000000-0000-0000-0000-000000000000",   "QuotaMb": 2048,   "WanAcceleratorUid": ""  } |

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

The example below creates a storage quota for the tenant account with ID c7bfad45-6089-4c47-89d4-6f707b82306b. The storage quota of 1024 MB is created on a backup repository that has ID 82db96c3-445c-4a7e-9587-f2d523e839f4.

|  |
| --- |
| Request:  POST https://localhost:9398/api/cloud/tenants/c7bfad45-6089-4c47-89d4-6f707b82306b/resources    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <CreateCloudTenantResourceSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Name>Cloud repository 3</Name>   <RepositoryUid>urn:veeam:Repository:82db96c3-445c-4a7e-9587-f2d523e839f4</RepositoryUid>   <QuotaMb>1024</QuotaMb>   <WanAcceleratorUid/> </CreateCloudTenantResourceSpec>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>CreateCloudTenantResource</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />     <Link Rel="Related" Type="CloudTenantResource" Href="https://localhost:9398/api/cloud/tenants/c7bfad45-6089-4c47-89d4-6f707b82306b/resources/37851b24-943f-4b07-939d-a93fca341a9e" Name="ABC Company" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>CreateCloudTenantResource</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
