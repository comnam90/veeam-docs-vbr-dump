---
title: "POST /agents/jobs/{ID}?action=toggleScheduleEnabled"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_agents_jobs_id_actiontogglescheduleenabled.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# POST /agents/jobs/{ID}?action=toggleScheduleEnabled


Disables or enables a Veeam Agent backup job having the specified ID. The Veeam Agent backup job is configured in Veeam Backup & Replication.

A disabled job remains in the list of Veeam Agent backup jobs on the backup server, but does not run according to specified job scheduling settings. To enable a job, perform the Disable operation once again.

Request

To disable or enable a Veeam Agent backup job, send the POST HTTP request to the /agents/jobs/{ID}?action=toggleScheduleEnabled URL.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/agents/jobs/{ID}?action=toggleScheduleEnabled |

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

The example below disables or enables a Veeam Agent backup job having ID 78c3919c-54d7-43fe-b047-485d3566f11f.

|  |
| --- |
| Request:  POST https://localhost:9398/api/agents/jobs/78c3919c-54d7-43fe-b047-485d3566f11f?action=toggleScheduleEnabled    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1"> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>UpdateJob</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |


