---
title: "post_jobs_id_linked_repositories"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_jobs_id_linked_repositories.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Adds a backup repository to a backup copy job with the specified ID.

|  |
| --- |
| Note |
| If a backup copy job contains linked backups, these linked backups will be removed after any edit operation (such as adding or removing a linked job or repository). |

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To add a backup repository to a backup copy job, send the POST HTTP request to the /jobs/{ID}/linkedBackupRepositories resource.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/jobs/{ID}/linkedBackupRepositories |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send the ID of the repository to be linked. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

The request body must contain the following element:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| LinkedBackupRepositoryUid | String | ID of a backup repository that you want to link to the backup copy job. | Yes | 1/1 |

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

The example below adds a backup repository to a backup copy job having ID d1b85018-2769-45be-89bc-03f66b60e6cb.

|  |
| --- |
| Request:  POST https://localhost:9398/api/jobs/d1b85018-2769-45be-89bc-03f66b60e6cb/linkedBackupRepositories    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Request Body:  <?xml version="1.0" encoding="utf-8"?>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>UpdateJob</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>UpdateJob</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
