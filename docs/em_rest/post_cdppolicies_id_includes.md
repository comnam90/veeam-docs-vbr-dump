---
title: "POST /cdpPolicies/{ID}/includes"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_cdppolicies_id_includes.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Adds a VM or a VM container to the CDP policy having the specified ID.

Request

To add a VM or VM container to the CDP policy, send the POST HTTP request to the /cdpPolicies/{ID}/includes resource.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/cdpPolicies/{ID}/includes |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters of the VM or VM container you want to add to the CDP policy. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| HierarchyObjRef | HierarchyObjRefType | Reference to the VM or VM container. You can [construct the reference manually](constructing_hierarchyobjreftype.md) or use the [lookup service](lookupsvc.md) to retrieve the reference. | Yes | 1/1 |
| HierarchyObjName | String | Name of the VM or VM container. | No | 1/1 |
| GuestProcessingOptions | GuestProcessing OptionsType | Options for application-aware image processing. For details, see  [Guest Processing Options](#guest). | Yes | 0/1 |

Guest Processing Options

You can define the following guest processing options for the CDP policy:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| VssSnapshotOptions | VssSnapshotOptionsType | Application-aware processing options. For details, see [Application-Aware Processing Options](#vss). | Yes | 0/1 |
| WindowsCredentialsId | String | Guest OS credentials for starting the indexing runtime process in Microsoft Windows OS. | Yes | 0/1 |
| LinuxCredentialsId | String | Guest OS credentials for starting the indexing runtime process in Linux OS. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "HierarchyObjRef": "urn:VMware:Vm:b4cd87e5-c608-4790-9178-076d16d4166b.vm-16",   "HierarchyObjName": "virt03-srv01",   "GuestProcessingOptions": {     "VssSnapshotOptions": {       "VssSnapshotMode": "RequireSuccess",       "IsCopyOnly": false     },     "WindowsCredentialsId": "00000000-0000-0000-0000-000000000000",     "LinuxCredentialsId": "00000000-0000-0000-0000-000000000000",   }  } |

Application-Aware Processing Options

You can define the following application-aware processing options for the CDP policy:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| VssSnapshotMode | String | Mode of application-aware image processing. Possible values:   * RequireSuccess * IgnoreFailures * Disabled | Yes | — |
| IsCopyOnly | Boolean | Defines whether copy-only backups must be created or transaction logs for Microsoft Exchange, Microsoft SQL and Oracle VMs must be processed. Possible values:   * True * False | Yes | 0/1 |
| UsePersistentGuestAgent | Boolean | Defines whether to use persistent guest agents on the protected VM for application-aware processing. Possible values:   * True * False   The default value is False. |  |  |

For example:

XML Representation

|  |
| --- |
| <VssSnapshotOptions>   <VssSnapshotMode>RequireSuccess</VssSnapshotMode>   <IsCopyOnly>false</IsCopyOnly>   <UsePersistentGuestAgent>false</UsePersistentGuestAgent> </VssSnapshotOptions> |

JSON Representation

|  |
| --- |
| "VssSnapshotOptions": {    "VssSnapshotMode": "RequireSuccess",    "IsCopyOnly": false,    "UsePersistentGuestAgent": false  } |

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

The example below adds a VM having MoID vm-10266 to the CDP policy having ID f365fbd8-fbd2-43ad-9f7a-c87cd390a0d9.

|  |
| --- |
| Request:  POST https://localhost:9398/api/cdpPolicies/f365fbd8-fbd2-43ad-9f7a-c87cd390a0d9/includes    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <CreateObjectInJobSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <HierarchyObjRef>urn:VMware:VM:00000000-0000-0000-0000-000000000000.vm-10266</HierarchyObjRef>   <HierarchyObjName>exch02</HierarchyObjName>   <GuestProcessingOptions>     <VssSnapshotOptions>       <VssSnapshotMode>RequireSuccess</VssSnapshotMode>       <IsCopyOnly>false</IsCopyOnly>       <UsePersistentGuestAgent>false</UsePersistentGuestAgent>     </VssSnapshotOptions>   </GuestProcessingOptions> </CreateObjectInJobSpec>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>UpdateCdpPolicy</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>UpdateCdpPolicy</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
