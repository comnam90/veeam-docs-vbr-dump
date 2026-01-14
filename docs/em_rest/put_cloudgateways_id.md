---
title: "put_cloudgateways_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/put_cloudgateways_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Edits settings of a cloud gateway with the specified ID.

Request

To edit settings of the cloud gateway, send the PUT HTTP request to the /cloud/gateways/{ID} resource.

HTTP Request

|  |
| --- |
| PUT https://<Enterprise-Manager>:9398/api/cloud/gateways/{ID} |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters for the cloud gateway whose settings must be updated. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Enabled | Boolean | Defines if the cloud gateway must be in the enabled or disabled state. Possible values:   * True * False | Yes | 0/1 |
| NetworkMode | CloudGatewayNetworking | Mode in which the cloud gateway must function. Possible values:   * Direct (if clients have a direct connection to the cloud gateway) * NAT (if the cloud gateway is located behind the NAT) | Yes | 1/1 |
| ExternalIP | String | External IP address of the NAT gateway. This parameter must be specified if the cloud gateway is located behind the NAT. | Yes | 1/1 |
| ExternalPort | UShort | TCP/IP port over which users' backup servers must communicate with the cloud gateway. By default, port 6180 is used. | Yes | 0/1 |
| InternalPort | UShort | Port on the NAT gateway used for listening to connections from users. By default, port 6180 is used. This parameter must be specified if the cloud gateway is located behind the NAT. | Yes | 0/1 |
| Description | String | Description for the cloud gateway. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "Enabled": true,   "NetworkMode": "Direct",   "ExternalIP": "172.16.13.97",   "ExternalPort": 6180,   "InternalPort": 6180,   "Description": "Cloud gateway 1",   "Name": "172.16.13.97",   "UID": "urn:veeam:CloudGateway:b5025a7b-5e13-41e2-a17e-9d9af985ecfd",   "Href": "https://localhost:9398/api/cloud/gateways/b5025a7b-5e13-41e2-a17e-9d9af985ecfd?format\u003dEntity",   "Type": "CloudGateway"  } |

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

The example below updates the description and external port settings for the cloud gateway having ID b5025a7b-5e13-41e2-a17e-9d9af985ecfd.

|  |
| --- |
| Request:  PUT https://localhost:9398/api/cloud/gateways/b5025a7b-5e13-41e2-a17e-9d9af985ecfd    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <CloudGateway Type="CloudGateway" Href="https://localhost:9398/api/cloud/gateways/b5025a7b-5e13-41e2-a17e-9d9af985ecfd?format=Entity" Name="172.16.13.97" UID="urn:veeam:CloudGateway:b5025a7b-5e13-41e2-a17e-9d9af985ecfd" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Enabled>true</Enabled>   <NetworkMode>Direct</NetworkMode>   <ExternalIP>172.16.13.97</ExternalIP>   <ExternalPort>6180</ExternalPort>   <InternalPort>6180</InternalPort>   <Description>Cloud gateway 1</Description> </CloudGateway>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>EditCloudGateway</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>EditCloudGateway</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
