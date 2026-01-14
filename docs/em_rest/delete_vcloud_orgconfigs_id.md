---
title: "delete_vcloud_orgconfigs_id"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/delete_vcloud_orgconfigs_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Deletes a VMware Cloud Director organization configuration with the specified ID.

|  |
| --- |
| Note |
| * You cannot delete a sample configuration with the name Other organizations. Instead, you can deactivate this configuration, that is, disable self-service backup for organizations that do not have individual configurations. For details, see [POST /vCloud/orgConfigs/{ID}?action=disable](post_vcloud_orgconfigs_id.md). * When you delete a VMware Cloud Director organization, you can specify whether to delete backup jobs and backups created for the organization as well. For details, see [Request Parameters](#options). |

Request

To remove a VMware Cloud Director organization configuration, send the DELETE HTTP request to the /vCloud/orgConfigs/{ID} resource.

HTTP Request

|  |
| --- |
| DELETE https://<Enterprise-Manager>:9398/api/vCloud/orgConfigs/{ID} |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Request Parameters

You can specify whether to delete backup jobs and backups created for the deleted organization. To do this, you must add the following parameters to the base URL of the request:

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| deleteJobs | Boolean | False | Defines if the backup jobs created for the organization will be deleted in Veeam Backup & Replication. Possible values:   * True * False |
| deleteBackupFiles | Boolean | False | Defines if the backups created for the organization will be deleted from the backup repository. Possible values:   * True * False |

You can use either of the parameters or both parameters at once. For example:

|  |
| --- |
| DELETE https://<Enterprise-Manager>:9398/api/vCloud/orgConfigs/39c5ea39-413e-4afa-8bea-78711d7f938d?deleteJobs=true |

or

|  |
| --- |
| DELETE https://<Enterprise-Manager>:9398/api/vCloud/orgConfigs/39c5ea39-413e-4afa-8bea-78711d7f938d?deleteBackupFiles=true |

or

|  |
| --- |
| DELETE https://<Enterprise-Manager>:9398/api/vCloud/orgConfigs/39c5ea39-413e-4afa-8bea-78711d7f938d?deleteJobs=true&deleteBackupFiles=true |

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

The example below removes a VMware Cloud Director organization configuration with ID ee1018b4-6f52-489e-80b7-8005e0b2d640.

|  |
| --- |
| Request:  DELETE https://localhost:9398/api/vCloud/orgConfigs/ee1018b4-6f52-489e-80b7-8005e0b2d640    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1"> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>DeleteVCloudOrganizationConfig</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
