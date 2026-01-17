---
title: "POST Method"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_method.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

The POST HTTP method is most often used to create a new resource: for example, a new logon session. However, in Veeam Backup Enterprise Manager REST API the POST HTTP method can be used for other activities, for example:

* Starting a job
* Cloning a job
* Downloading a file
* Restoring a VM

Some POST HTTP requests do not require a request body. For example, if you want to start a job, send a request of the following type:

|  |
| --- |
| POST https://localhost:9398/api/jobs/{ID}?action=start |

Other POST HTTP requests require the request body. For example, if you want to clone a job in Veeam Backup Enterprise Manager, send the HTTP POST request and communicate to the server the parameters for the cloned job in the request body. The body of the request must conform to the [XML Schema](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API:

|  |
| --- |
| Request:  POST https://localhost:9398/api/jobs/568c42ce-eb11-4140-92cf-39ab36712bf5?action=clone    Request Body:  <?xml version="1.0" encoding="utf-8"?> |

In case of success, the server returns the HTTP response code 202 Accepted. The operation itself is performed in the asynchronous manner. The server creates a task for the operation completion and returns a link to this task to the client. Using this link, the client can monitor the task completion.

The example below illustrates the job start operation:

|  |
| --- |
| Request:  POST https://localhost:9398/api/jobs/115f560f-3a5f-4a88-b0c8-096c845bafcd?action=start    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-10"> <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-10" />   </Links>   <TaskId>task-10</TaskId>   <State>Running</State>   <Operation>StartJob</Operation> </Task> |

To monitor the state of the task completion, the client sends the GET HTTP request to the task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-10    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-10">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-10" />   </Links>   <TaskId>task-10</TaskId>   <State>Finished</State>   <Operation>StartJob</Operation>   <Result Success="true">     <Message>Job "SQL Backup" triggered to start.</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
