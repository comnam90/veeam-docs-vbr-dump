---
title: "GET /tasks/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_tasks_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# GET /tasks/{ID}


Returns a resource representation of a task having the specified ID. The task is created by Veeam Backup Enterprise Manager in response to client requests.

Request

To get a task having the specified ID, send the GET HTTP request to the /tasks/{ID} resource.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/tasks/{ID} |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 200 OK.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns the /tasks/{ID} resource that contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| TaskId | String | ID of the task resource, for example: task-1. |
| State | String | State of the task. Possible values:   * Running — the task is in progress. * OperationFinished — the task operation is finished on the backup server, but Veeam Backup Enterprise Manager has not collected the operation data yet. * Finished — the task operation is finished, and the Veeam Backup Enterprise Manager database contains the operation data. |
| Operation | String | Name of the task operation, for example: StartJob. |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=Task](get_query_task.md).

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /tasks/{ID} | Delete | URL for the [DELETE /task/{ID}](delete_task_id.md) request. |

Examples

* The example below returns the task-1 task with the Running state.

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1"> |

* The example below returns the task-2 task with the OperationFinished state.

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-2    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-2">   <Links>     <Link Rel="Delete" Href="https://localhost:9398/api/tasks/task-2" />   </Links>   <TaskId>task-2</TaskId>   <State>OperationFinished</State>   <Operation>StartJob</Operation>   <Result Success="true">     <Message>OperationFinished</Message>   </Result> </Task> |

* The example below returns the task-3 task with the Finished state.

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-3    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-3">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-3" />   </Links>   <TaskId>task-3</TaskId>   <State>Finished</State>   <Operation>StartJob</Operation>   <Result Success="true">     <Message>Job "SQL Server Replication" triggered to start.</Message>   </Result> </Task> |


