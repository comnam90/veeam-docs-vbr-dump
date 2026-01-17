---
title: "POST /agents/agentRestorePoints/{ID}/mounts"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_agents_agentrestorepoints_id_mounts.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Starts the machine guest OS files restore from the specified restore point. Disks of the restored machine are mounted to the backup server and the machine guest OS files become available under the C:\VeeamFLR\<vm-name> folder.

Request

To start the machine guest OS files restore, send the POST HTTP request to the /agents/agentRestorePoints/{ID}/mounts URL.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/agents/agentRestorePoints/{ID}/mounts |

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

The example below restores machine guest OS files from the restore point having ID 710c0a5f-2783-4222-b669-0da996b09b97:

|  |
| --- |
| Request:  POST https://localhost:9398/api/agents/agentRestorePoints/710c0a5f-2783-4222-b669-0da996b09b97/mounts    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  202 Accepted    Response Body:  <Task Href="http://local.host:9399/api/tasks/task-1" Type="Task" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Tasks xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Task Href="https://localhost:9398/api/tasks/task-5" Type="Task">     <Links>       <Link Href="https://localhost:9398/api/tasks/task-5" Rel="Delete"/>       <Link Href="https://localhost:9398/api/agents/agentRestorePoints/dd3cf3d0-0533-424e-abc3-249c4c62b797/mounts/1" Name="dd3cf3d0-0533-424e-abc3-249c4c62b797@1" Type="AgentRestorePointMount" Rel="Related"/>     </Links>     <TaskId>task-5</TaskId>     <State>Finished</State>     <Operation>MountRestorePoint</Operation>     <Result Success="true">       <Message>Ok</Message>     </Result>   </Task> </Tasks> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
