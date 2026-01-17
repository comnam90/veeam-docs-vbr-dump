---
title: "DELETE /cloud/tenants/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/delete_tenants_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Deletes a tenant account with the specified ID from the backup server connected to Veeam Backup Enterprise Manager.

|  |
| --- |
| Note |
| When you delete a tenant account, you can specify whether to delete backups created by the tenant in the cloud repository. For details, see [Request Parameters](#options). |

Request

To remove a tenant account, send the DELETE HTTP request to the /cloud/tenants/{ID} resource.

HTTP Request

|  |
| --- |
| DELETE https://<Enterprise-Manager>:9398/api/cloud/tenants/{ID} |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Request Parameters

You can specify whether to delete backups created for the deleted tenant account. To do this, you must add the following parameter to the base URL of the request:

| Element | Type | Required | Description |
| --- | --- | --- | --- |
| includeBackups | Boolean | False | Defines if the backups created for the tenant account will be deleted from the cloud repository. Possible values:   * True * False |

For example:

|  |
| --- |
| DELETE https://localhost:9398/api/cloud/tenants/6f17f70a-a61c-4ef0-ac7f-426a6ae1ec8b?includeBackups=true |

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

The example below removes a tenant account with ID 6f17f70a-a61c-4ef0-ac7f-426a6ae1ec8b.

|  |
| --- |
| Request:  DELETE https://localhost:9398/api/cloud/tenants/6f17f70a-a61c-4ef0-ac7f-426a6ae1ec8b    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1"> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>DeleteCloudTenant</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
