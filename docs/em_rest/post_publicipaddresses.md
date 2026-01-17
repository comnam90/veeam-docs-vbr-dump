---
title: "POST /cloud/publicIpAddresses"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_publicipaddresses.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Adds one or several public IP addresses to the pool of public IP addresses configured on the backup server connected to Veeam Backup Enterprise Manager.

Request

To add one or several public IP addresses to the pool of public IP addresses, send the POST HTTP request to the /cloud/publicIpAddresses resource.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/cloud/publicIpAddresses |

Request Header

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters for the new public IP address range. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| BackupServerUid | UidType | UID of the backup server on which the pool of public IP addresses must be configured. | No | 1/1 |
| IpAddressLowerBound | String | The first IP address in the range of public IP addresses added to the pool. | Yes | 1/1 |
| IpAddressUpperBound | String | The last IP address in the range of public IP addresses added to the pool. | Yes | 1/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "BackupServerUid": "urn:veeam:BackupServer:8fff3b8e-c3f1-4ef5-aecc-561f07bf9982\n",   "IpAddressLowerBound": "198.51.100.11",   "IpAddressUpperBound": "198.51.100.15"  } |

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

The example adds a range of public IP addresses to the pool of public IP addresses on the backup server with ID 8fff3b8e-c3f1-4ef5-aecc-561f07bf9982.

|  |
| --- |
| Request:  POST https://localhost:9398/api/cloud/publicIpAddresses    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <CloudPublicIpAddressCreateSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <BackupServerUid>urn:veeam:BackupServer:8fff3b8e-c3f1-4ef5-aecc-561f07bf9982 </BackupServerUid>   <IpAddressLowerBound>198.51.100.11</IpAddressLowerBound>   <IpAddressUpperBound>198.51.100.15</IpAddressUpperBound> </CloudPublicIpAddressCreateSpec>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>CreateCloudPublicIpAddress</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />     <Link Rel="Related" Type="CloudPublicIpAddressList" Href="https://localhost:9398/api/cloud/publicIpAddresses?format=Entity" />    </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>CreateCloudPublicIpAddress</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
