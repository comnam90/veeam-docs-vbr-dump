---
title: "post_backupservers_id_quickbackup"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_backupservers_id_quickbackup.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Creates a quick backup of a VM on a backup server added to Veeam Backup Enterprise Manager. Quick backup is an incremental backup of a VM processed by a backup job. To create quick backups for multiple VMs, use separate requests for each VM.

Request

To create an incremental backup for a VM, send the POST HTTP request to the /backupServers/{ID}?action=quickbackup resource.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/backupServers/{ID}?action=quickbackup |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters of the quick backup task. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| VmRef | HierarchyObjRefType | Reference to a VM for which an incremental backup must be created. You can [construct the reference manually](constructing_hierarchyobjreftype.md) or use the [lookup service](lookupsvc.md) to retrieve the reference. | No | 1/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "VmRef": "urn:VMware:Vm:02bd0847-f522-4670-90eb-10312498809d.vm-80225"  } |

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

The example below creates an incremental backup for a VM having MoID vm-80220 on the backup server having ID f365fbd8-fbd2-43ad-9f7a-c87cd390a0d9.

|  |
| --- |
| Request:  POST https://localhost:9398/api/backupServers/f365fbd8-fbd2-43ad-9f7a-c87cd390a0d9?action=quickbackup    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <QuickBackupStartupSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">    <VmRef>urn:VMware:Vm:02bd0847-f522-4670-90eb-10312498809d.vm-80225</VmRef> </QuickBackupStartupSpec>    Response:  202 Created    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>QuickBackup</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />     <Link Rel="Related" Type="BackupJobSession" Href="https://localhost:9398/api/backupSessions/d34e76fb-86d6-41e9-b84f-88a87b52e07a?format=Entity" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>QuickBackup</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
