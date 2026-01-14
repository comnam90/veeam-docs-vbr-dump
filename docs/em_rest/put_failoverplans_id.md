---
title: "put_failoverplans_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/put_failoverplans_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Edits a failover plan having the specified ID.

Request

To edit a failover plan, send the PUT HTTP request to the /failoverPlans/{ID} resource.

HTTP Request

|  |
| --- |
| PUT https://<Enterprise-Manager>:9398/api/failoverPlans/{ID} |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters for the failover plan that must be updated. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Description | String | Description of the failover plan. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "Description": "Created by My failover plan",   "Name": "SQL Failover Plan",   "UID": "urn:veeam:FailoverPlan:ae01e36f-32a3-4095-95fa-09a2af744009",   "Href": "https://localhost:9398/api/failoverPlans/ae01e36f-32a3-4095-95fa-09a2af744009?format\u003dEntity",   "Type": "FailoverPlan"  } |

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

The example below updates the description parameter in the failover plan having ID ae01e36f-32a3-4095-95fa-09a2af744009.

|  |
| --- |
| Request:  PUT https://localhost:9398/api/failoverPlans/ae01e36f-32a3-4095-95fa-09a2af744009    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <FailoverPlan Type="FailoverPlan" Href="https://localhost:9398/api/failoverPlans/ae01e36f-32a3-4095-95fa-09a2af744009?format=Entity" Name="SQL Failover Plan" UID="urn:veeam:FailoverPlan:ae01e36f-32a3-4095-95fa-09a2af744009" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Description>Created by My failover plan</Description> </FailoverPlan>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>EditFailoverPlan</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>EditFailoverPlan</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
