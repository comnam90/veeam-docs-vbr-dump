---
title: "POST /cdpReplica/vApps/{ID}?action=failover"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_cdpreplicavapp_id_actionfailover.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# POST /cdpReplica/vApps/{ID}?action=failover


Starts the failover process of the specified vApp to its CDP replica.

Request

To start the VM replica failover process, send the POST HTTP request to the /cdpReplica/vApps/{ID}?action=failover URL.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/cdpReplica/vApps/{ID}?action=failover |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send the parameters for the failover. The body of the request must conform to the  [XML Schema Definitionem\_rest\_](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the elements you want to specify. You can define the following general parameters:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| RestoreCurrent | Boolean | Defines whether Veeam Backup & Replication will fail over the vApp to their latest crush-consistent restore point. Possible values:   * True * False | Yes | 1/1 |
| RestoreCurrentVss | Boolean | Defines whether Veeam Backup & Replication will fail over the vApp to their latest long-term application-consistent restore points. Possible values:   * True * False | Yes | 1/1 |
| RestoreAtInterval | DateTime | If you specify this parameter, Veeam Backup & Replication will fail over the vApp to the most recent restore point in the interval that includes the selected date. The parameter accepts only UTC-formatted DateTime values. | Yes | 0/1 |
| RestoreAtPointinTime | DateTime | If you specify this parameter, Veeam Backup & Replication will fail over the vApp to the most recent replicated state that was created prior to the selected date. The parameter accepts only UTC-formatted DateTime values. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "RestoreCurrent": true,   "RestoreCurrentVss": false,   "RestoreAtPointInTime": "2023-02-17T15:31:40"  } |

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

In the response body, the REST API returns a task that has been created to perform the requested operation. To track the status of the operation, send the [GET /tasks/{ID}](get_tasks_id.md) request.

The task resource also contains a link to the task deletion operation. To stop the task execution, send the [DELETE /task/{ID}](delete_task_id.md) request to the URL in the link.

Example

The example below starts the failover process for the vApp that has ID e809a086-2562-4a0f-a9a8-9c115ff8f0ba.

|  |
| --- |
| Request:  POST https://localhost:9398/api/cdpReplica/vApps/e809a086-2562-4a0f-a9a8-9c115ff8f0ba?action=failover    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Request Body:  <?xml version="1.0" encoding="utf-8"?> <CdpFailoverStartSpec xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">   <RestoreCurrent>true</RestoreCurrent>   <RestoreCurrentVss>false</RestoreCurrentVss>   <RestoreAtInterval>2023-02-17T15:31:40</RestoreAtInterval> </CdpFailoverStartSpec>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>StartFailover</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />     <Link Rel="Related" Type="RestoreSession" Href="https://localhost:9398/api/restoreSessions/2abbd1f7-647a-46b7-9f39-6e84ea31802b?format=Entity" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>StartFailover</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |


