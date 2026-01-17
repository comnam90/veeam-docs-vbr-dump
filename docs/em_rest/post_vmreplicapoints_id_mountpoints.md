---
title: "POST /vmReplicaPoints/{ID}/mounts"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_vmreplicapoints_id_mountpoints.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# POST /vmReplicaPoints/{ID}/mounts


Starts the VM guest OS files restore from the specified VM replica restore point. Disks of the restored VM are mounted to the backup server and the VM guest OS files become available in the C:\VeeamFLR\<vm-name> folder.

Veeam Backup & Replication detects guest OS on the mounted backup automatically. With Veeam Backup Enterprise Manager REST API you can define the type of the guest OS manually. If you do not define the type of the guest OS manually, Veeam Backup Enterprise Manager will use the default value. The default value for the guest OS is Windows.

Request

To start VM guest OS files restore, send the POST HTTP request to the /vmReplicaPoints/{ID}/mounts URL.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/vmReplicaPoints/{ID}/mounts |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send the parameters for the mounted backup. The body of the request must conform to the  [XML Schema Definitionem\_rest\_](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the elements you want to specify. You can define the following general parameters for the mount:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| OsKind | String | Specifies the guest OS:   * Linux * Windows | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "OsKind": "Windows"  } |

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

The example below restores VM replica guest OS files from the restore point having ID 7b8f9c7d-4e73-429a-9fc6-1ad2c58902bc:

|  |
| --- |
| Request:  POST https://localhost:9398/api/vmReplicaPoints/710c0a5f-2783-4222-b669-0da996b09b97/mounts    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>MountRestorePoint</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />     <Link Rel="Related" Type="VmRestorePointMount" Href="https://localhost:9398/api/vmRestorePoints/623cbbec-c8ff-4cf4-96be-d433f3b775c7/mounts/1" Name="623cbbec-c8ff-4cf4-96be-d433f3b775c7@1" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>MountRestorePoint</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |


