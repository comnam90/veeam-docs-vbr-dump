---
title: "POST /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/{filepath}?action=restore"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_catalog_vms_vmname_vmrestorepoints_id_guestfs_filepath.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Starts restore of the specified VM guest OS file or folder from the specified restore point. The file or folder is restored to its original location.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* Microsoft Hyper-V

Request

To restore a specific VM guest OS file or folder, send the POST HTTP request to the /catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/{filepath}?action=restore URL.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/catalog/vms/{vmname}/vmRestorePoints/{ID}/guestfs/{filepath}?action=restore |

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

The example below lets the client restore the C:/Users folder from the VM guest OS:

|  |
| --- |
| Request:  POST https://localhost:9398/api/catalog/vms/exch01/vmRestorePoints/1bd3ebf0-34fa-40f6-bc4c-c9bacdba8c0a/guestfs/C:/Users?action=restore    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1"> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Href="https://localhost:9398/api/tasks/task-1" />     <Link Rel="Related" Type="RestoreSession" Href="https://localhost:9398/api/restoreSessions/8f20b44a-b96f-47c6-9a17-ba9d1c17a342?format=Entity" Name="Restore job session" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>RestoreFile</Operation>   <Result Success="true">     <Message>Restore operations started successfully.</Message>   </Result> </Task> |

To monitor the restore session progress, find the necessary link component in the resource representation of the task and send the GET HTTP request to the https://<Enterprise-Manager>:9398/api/restoreSessions/{ID}?format=Entity URL:

|  |
| --- |
| Request:  GET https://localhost:9398/api/restoreSessions/8f20b44a-b96f-47c6-9a17-ba9d1c17a342?format=Entity    Request Header:  X-RestSvcSessionId:   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <RestoreSession xmlns="http://www.veeam.com/ent/v1.0" Type="RestoreSession" Href="https://localhost:9398/api/restoreSessions/8f20b44a-b96f-47c6-9a17-ba9d1c17a342?format=Entity" Name="FLR\_[fileserver01]@2017-01-12 16:54:40" UID="urn:veeam:RestoreSession:8f20b44a-b96f-47c6-9a17-ba9d1c17a342" VmDisplayName="fileserver01">   <Links>     <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/be21c981-7353-4896-8b69-0bf300c05337" Name="172.17.53.1" />     <Link Rel="Alternate" Type="RestoreSessionReference" Href="https://localhost:9398/api/restoreSessions/8f20b44a-b96f-47c6-9a17-ba9d1c17a342" Name="FLR\_[fileserver01]@2017-01-12 16:54:40" />     <Link Rel="Related" Type="VmRestorePointReference" Href="https://localhost:9398/api/vmRestorePoints/d2bfab92-7286-454e-ada5-55dd8146d462" Name="filesever01@2017-01-06 07:59:00" />   </Links>   <JobType>FileLevelRestore</JobType>   <CreationTimeUTC>2017-01-12T16:54:40Z</CreationTimeUTC>   <EndTimeUTC>2017-01-12T16:56:28.7Z</EndTimeUTC>   <State>Stopped</State>   <Result>Success</Result>   <Progress>100</Progress> </RestoreSession> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
