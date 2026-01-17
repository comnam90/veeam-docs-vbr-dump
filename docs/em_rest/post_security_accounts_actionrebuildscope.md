---
title: "POST /security/accounts?action=rebuildScope"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_security_accounts_actionrebuildscope.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Rebuilds a restore scope for user accounts added to Veeam Backup Enterprise Manager.

Veeam Backup Enterprise Manager periodically rescans the virtual infrastructure to get the latest data about the virtual infrastructure hierarchy and rebuild the restore scope for user accounts. The rescan procedure is performed automatically once a day. You can start the rebuild scope operation manually when you need to perform rescan. For example, you can perform this operation in case new VMs have been created and you want to immediately include them to the restore scope for some users.

Request

To rebuild a restore scope for a user account, send the POST HTTP request to the /security/accounts?action=rebuildScope resource.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/security/accounts?action=rebuildScope |

Request Header

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters of the restore scope rebuild process. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain one of the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| RebuildAll | — | Rebuilds a restore scope for all user accounts added to Veeam Backup Enterprise Manager. | No | — |
| RebuildUnprocessed | — | Rebuilds a restore scope for user accounts whose restore scope has been changed since the previous scope rebuild operation. This may be helpful if a restore scope was changed for some users but was not automatically refreshed for some reason. | No | — |
| RebuildForCurrentUser | — | Rebuilds a restore scope for the user account that is currently logged on to Veeam Backup Enterprise Manager. This may be helpful if some newly created VMs and backups are not yet displayed to a user right after the new logon session is created. | No | — |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "RebuildUnprocessed": {}  } |

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 201 Created.

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

The example below rebuilds the restore scope for all users currently added to Veeam Backup Enterprise Manager.

|  |
| --- |
| Request:  POST https://localhost:9398/api/security/accounts?action=rebuildScope    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <RebuildScopeJobSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <RebuildUnprocessed/> </RebuildScopeJobSpec>    Response:  201 Created    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>StartRebuildScope</Operation>   <Result Success="true" /> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
