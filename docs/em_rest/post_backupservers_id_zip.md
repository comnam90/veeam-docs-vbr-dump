---
title: "POST /backupServers/{ID}?action=veeamzip"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_backupservers_id_zip.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Creates a VeeamZIP file for one or several VMs on the backup server added to Veeam Backup Enterprise Manager.

|  |
| --- |
| Note |
| You can use Veeam Backup Enterprise Manager REST API to create VeeamZIP files for VMware vSphere VMs only. To create VeeamZIP files for Microsoft Hyper-V VMs, use the Veeam Backup & Replication console. |

Request

To create a VeeamZIP file for one or several VMs on the backup server, send the POST HTTP request to the /backupServers/{ID}?action=veeamzip resource.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/backupServers/{ID}?action=veeamzip |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters of the VeeamZIP task. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| VmRef | HierarchyObjRefType | Reference to a VM or VMs for which a VeeamZIP file must be created. You can [construct the reference manually](constructing_hierarchyobjreftype.md) or use the [lookup service](lookupsvc.md) to retrieve the reference. | No | 1/- |
| RepositoryUid | UidType | UID of the backup repository on which the VeeamZIP file must be created. | No | 1/1 |
| PasswordKeyId | String | ID of the password that must be used to encrypt the VeeamZIP file, for example: aeab2c41-fbb1-4d67-83a9-00e269b777c7. Password IDs containing 32 digits with 4 dashes are displayed in the representation of the /backupServers/{ID}/passwords/{ID} resource. | Yes | 0/1 |
| CompressionLevel | Int | Compression level that must be used to create the VeeamZIP file. Possible values:   * 1 — No compression * 2 — Dedupe-friendly * 3 — Optimal * 4 — High * 5 — Extreme | No | 1/1 |
| DisableGuestQuiescence | Boolean | By default, before creating a VeeamZIP file, Veeam Backup & Replication quiesces the VM file system with application-aware image processing. Application-aware image processing helps create transactionally consistent VeeamZIP files. To disable application-aware image processing for processed VMs, set this parameter to True. | No | 0/1 |
| BackupRetention | FreeBackupRetention | Period of time for which the created VeeamZIP file must be retained on the backup repository. Possible values:   * Never * Tonight * TomorrowNight * In3days * In1Week * In2Weeks * In1Month  * In3Months * In6Months * In1Year * In2Years * In3Years * In5Years * In7Years   The In5Years and In7Years values are available starting from Veeam Backup Enterprise Manager 11a (build 11.0.1.1261). | No | 1/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "VmRef": "urn:VMware:Vm:a9850703-e3fd-43d8-8f30-6d7fba40b6dd.vm-38856",   "RepositoryUid": "urn:veeam:Repository:b609c947-dd30-4295-8b57-cc880329dbd6",   "PasswordKeyId": "aeab2c41-fbb1-4d67-83a9-00e269b777c7",   "CompressionLevel": 5,   "DisableGuestQuiescence": false,   "BackupRetention": "Never"  } |

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

The example below creates a VeeamZIP fie for a VM having MoID vm-10266 on the backup server having ID f365fbd8-fbd2-43ad-9f7a-c87cd390a0d9.

|  |
| --- |
| Request:  POST https://localhost:9398/api/backupServers/f365fbd8-fbd2-43ad-9f7a-c87cd390a0d9?action=veeamzip    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <VeeamZipStartupSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <VmRef>urn:VMware:vm:bffeb9f5-1bdd-4bbd-9299-6fcb7c37bdf6.vm-10266</VmRef>   <RepositoryUid>urn:veeam:Repository:b609c947-dd30-4295-8b57-cc880329dbd6</RepositoryUid>   <PasswordKeyId>aeab2c41-fbb1-4d67-83a9-00e269b777c7</PasswordKeyId>   <CompressionLevel>5</CompressionLevel>   <DisableGuestQuiescence>false</DisableGuestQuiescence>   <BackupRetention>Never</BackupRetention> </VeeamZipStartupSpec>    Response:  202 Success    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>VeeamZip</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />     <Link Rel="Related" Type="BackupJobSession" Href="https://localhost:9398/api/backupSessions/d34e76fb-86d6-41e9-b84f-88a87b52e07a?format=Entity" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>VeeamZip</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
