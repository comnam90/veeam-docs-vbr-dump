---
title: "put_publicipaddresses_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/put_publicipaddresses_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Edits settings of a public IP address resource with the specified ID.

Request

To edit settings of the public IP address resource, send the PUT HTTP request to the /cloud/publicIpAddresses/{ID} resource.

HTTP Request

|  |
| --- |
| PUT https://<Enterprise-Manager>:9398/api/cloud/publicIpAddresses/{ID} |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters for the public IP address resource whose settings must be updated. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| IpAddress | String | Public IP address, for example: 198.51.100.22. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "IpAddress": "198.51.100.22",   "BackupServerUid": "urn:veeam:BackupServer:8fff3b8e-c3f1-4ef5-aecc-561f07bf9982",   "Name": "198.51.100.22",   "UID": "urn:veeam:CloudPublicIpAddress:22d2cdad-ddd1-4789-9e27-03bf25786648",   "Href": "https://localhost:9398/api/cloud/publicIpAddresses/22d2cdad-ddd1-4789-9e27-03bf25786648?format\u003dEntity",   "Type": "CloudPublicIpAddress"  } |

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 204 No Content.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

None.

Example

The example below updates the IP address for the public IP address resource with ID 22d2cdad-ddd1-4789-9e27-03bf25786648.

|  |
| --- |
| Request:  PUT https://localhost:9398/api/cloud/publicIpAddresses/22d2cdad-ddd1-4789-9e27-03bf25786648    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <CloudPublicIpAddress Type="CloudPublicIpAddress" Href="https://localhost:9398/api/cloud/publicIpAddresses/22d2cdad-ddd1-4789-9e27-03bf25786648?format=Entity" Name="198.51.100.22" UID="urn:veeam:CloudPublicIpAddress:22d2cdad-ddd1-4789-9e27-03bf25786648" BackupServerUid="urn:veeam:BackupServer:8fff3b8e-c3f1-4ef5-aecc-561f07bf9982" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <IpAddress>198.51.100.22</IpAddress> </CloudPublicIpAddress>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>EditCloudPublicIpAddress</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>EditCloudPublicIpAddress</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
