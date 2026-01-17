---
title: "POST /cloud/gateways"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_gateways.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Configures a new cloud gateway on the backup server connected to Veeam Backup Enterprise Manager.

To configure a cloud gateway, Veeam Backup & Replication assigns the cloud gateway role to a Microsoft Windows server. Note that the Microsoft Windows server must be added to the backup infrastructure beforehand.

Request

To create a new cloud gateway, send the POST HTTP request to the /cloud/gateways resource.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/cloud/gateways |

Request Header

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters for the new cloud gateway. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| BackupServerIdOr | String | UID or DNS name of the backup server on which the cloud gateway must be created.  This parameter is supported by previous versions of Veeam Backup Enterprise Manager REST API. In current version of REST API, it is recommended that the new [BackupServerUid](post_gateways.md#BackupServerUid) parameter is used in the request body. | No | 0/1 |
| ServerHostName | String | DNS name or IP address of the Microsoft Windows server to which the cloud gateway role must be assigned. | Yes | 1/1 |
| Description | String | Description for the cloud gateway. | Yes | 0/1 |
| ExternalIp | String | External IP address of the NAT gateway. This parameter must be specified if the cloud gateway is located behind the NAT. | Yes | 0/1 |
| ExternalPort | UShort | TCP/IP port over which users' backup servers must communicate with the cloud gateway. By default, port number 6180 is used. | Yes | 0/1 |
| NetworkType | CloudGatewayNetworking | Mode in which the cloud gateway must function. Possible values:   * Direct (if clients have a direct connection to the cloud gateway) * NAT (if the cloud gateway is located behind the NAT) | Yes | 1/1 |
| InternalPort | UShort | Port on the NAT gateway used for listening to connections from users. By default, port 8080 is used. This parameter must be specified if the cloud gateway is located behind the NAT. | Yes | 0/1 |
| BackupServerUid | UID | UID of the backup server on which the cloud gateway must be created. | No | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> <CreateCloudGatewaySpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <ServerHostName>srv01.tech.local</ServerHostName>   <Description>Cloud gateway server 01</Description>   <ExternalPort>6180</ExternalPort>   <NetworkType>Direct</NetworkType>   <InternalPort>6180</InternalPort>   <BackupServerUid>urn:veeam:BackupServer:29e5d158-1f58-44bc-bbaa-2752d787a91d</BackupServerUid> </CreateCloudGatewaySpec> |

JSON Representation

|  |
| --- |
| {   "ServerHostName": "srv01.tech.local",   "Description": "Cloud gateway server 01",   "ExternalPort": 6180,   "NetworkType": "Direct",   "InternalPort": 6180,   "BackupServerUid": "urn:veeam:BackupServer:29e5d158-1f58-44bc-bbaa-2752d787a91d"  } |

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

The example below creates a cloud gateway on the backup server having UID urn:veeam:BackupServer:29e5d158-1f58-44bc-bbaa-2752d787a91d. The cloud gateway role is assigned to a Microsoft Windows machine that has IP address 172.16.13.119.

|  |
| --- |
| Request:  POST https://localhost:9398/api/cloud/gateways    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <CreateCloudGatewaySpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <ServerHostName>172.16.13.119</ServerHostName>   <Description>Cloud gateway server 01</Description>   <ExternalPort>6180</ExternalPort>   <NetworkType>Direct</NetworkType>   <InternalPort>6180</InternalPort>   <BackupServerUid>urn:veeam:BackupServer:29e5d158-1f58-44bc-bbaa-2752d787a91d</BackupServerUid> </CreateCloudGatewaySpec>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>CreateCloudGateway</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />     <Link Rel="Related" Type="CloudGateway" Href="https://localhost:9398/api/cloud/gateways/917be225-6744-4777-8096-cbabaec55006?format=Entity" Name="" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>CreateCloudGateway</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
