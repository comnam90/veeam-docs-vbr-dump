---
title: "put_method"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/put_method.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

The PUT HTTP method is used to update the properties of the resource, for example, edit job settings.

The PUT HTTP method requires a request body. In the body of the request, the client must send an updated representation of the resource. The body may contain the whole resource representation or only those settings that the client wants to edit. The body of the request must conform to the [XML Schema](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

In case of success, the PUT HTTP method returns the HTTP response code 200 OK or 202 Accepted.

* Code 200 OK is returned if the operation can be performed immediately.
* Code 202 Accepted is returned if the operation takes much time to perform. In this case, the operation is performed in the asynchronous manner. The server creates a task for method completion and returns a link to this task to the client. Using this link, the client can monitor the task completion.

In the example below, the PUT HTTP request is sent to update the job description:

|  |
| --- |
| Request:  PUT https://localhost:9398/api/jobs/115f560f-3a5f-4a88-b0c8-096c845bafcd    Request Body:  <?xml version="1.0" encoding="utf-8"?>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-12"> <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-12" />   </Links>   <TaskId>task-12</TaskId>   <State>Running</State>   <Operation>EditJob</Operation> </Task> |

To monitor the state of the task completion, the client sends the GET HTTP request to the task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-12    Response:  20O Success    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-12"> <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-12" />   </Links>   <TaskId>task-12</TaskId>   <State>Finished</State>   <Operation>EditJob</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
