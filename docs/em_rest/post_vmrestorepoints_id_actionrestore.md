---
title: "post_vmrestorepoints_id_actionrestore"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_vmrestorepoints_id_actionrestore.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Starts the entire VM restore process from the restore point having the specified ID.

Supported Platforms

The request is supported for the following platforms:

* VMware vSphere
* VMware Cloud Director
* Microsoft Hyper-V

Request

To start the entire VM restore, send the POST HTTP request to the /vmRestorePoints/{ID}/?action=restore URL.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/vmRestorePoints/{ID}?action=restore |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send the parameters for the entire VM restore. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

Depending on the platform on which the restored VM is created, the request body may contain different elements.

For VMware and Hyper-V platforms, the request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| PowerOnAfter | Boolean | Specifies if the VM must be powered on after the restore process is complete. | Yes | 1/1 |
| QuickRollback | Boolean | Specifies if Veeam Backup & Replication must use the incremental restore functionality to recover the VM. During incremental restore, Veeam Backup & Replication queries CBT to get data blocks that are necessary to revert the VM to an earlier point in time, and will restore only these data blocks from the backup. Incremental restore significantly reduces the restore time and has little impact on the production environment. | Yes | 1/1 |
| KeepOriginalVM | Boolean | Specifies if the original VM must be preserved on the host along with the restored VM.  Note: If this option is set to true, the QuickRollback option must be set to false. | Yes | 0/1 |

For the VMware Cloud Director platform, the request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| PowerOnAfterRestore | Boolean | Specifies if the VM must be powered on after the restore process is complete. | Yes | 1/1 |
| HierarchyRootUid | UID | ID of the host on which the VM should be restored, for example: urn:veeam:HierarchyRoot:fa099d3b-7376-49b1-884c-bb6fa47c7b1e. | Yes | 1/1 |
| VmsRestoreParameters | vCloudVmRestoreParametersInfo | Defines [VM-specific parameters](post_vmrestorepoints_id_actionrestore.md#params). | No | — |

VMs Restore Parameters

VM restore parameters are provided in the following format:

XML Representation

|  |
| --- |
| <VmRestoreParameters> |

JSON Representation

|  |
| --- |
| "VmRestoreParameters": {   "VmRestorePointUid": "urn:veeam:VmRestorePoint:48c8cd65-d5fa-4ca6-8a98-d3fde641086e",   "VmNewName": "vmTestSize",   "DatastoreRef": "urn:vCloud:Datastore:fa099d3b-7376-49b1-884c-bb6fa47c7b1e.urn:vcloud:datastore:68d9f62d-f3c1-4842-8ad6-9b7faca3c92a",   "OrgVdcStorageProfileRef": "urn:vCloud:OrgVdcStorageProfile:fa099d3b-7376-49b1-884c-bb6fa47c7b1e.urn:vcloud:vdcstorageprofile:1afeb3cc-bc4f-4e0f-b092-a3f8bbe70adc",   "LinkedCloneVmTemplateRef": ""  } |

You can define the following restore parameters for VMs:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| VmRestorePointUid | UID | ID of the restore point from which the VM should be restored, for example: urn:veeam:VmRestorePoint:48c8cd65-d5fa-4ca6-8a98-d3fde641086e. | Yes | 1/1 |
| VmNewName | String | Name of the restored VM. If this parameter is not specified, the VM is restored with its initial name. | Yes | 0/1 |
| DatastoreRef | HierarchyObjRefType | Reference to the datastore on which VM files should be placed. You can [construct the reference manually](constructing_hierarchyobjreftype.md) or use the [lookup service](lookupsvc.md) to retrieve the reference. | Yes | 0/1 |
| OrgVdcStorageProfileRef | HierarchyObjRefType | Reference to the OrgVdc profile to be used for the restored VM. You can [construct the reference manually](constructing_hierarchyobjreftype.md) or use the [lookup service](lookupsvc.md) to retrieve the reference. | Yes | 0/1 |
| LinkedCloneVmTemplateRef | HierarchyObjRefType | (For linked clone VMs) Reference to the template that was used to create the VM. You can [construct the reference manually](constructing_hierarchyobjreftype.md) or use the [lookup service](lookupsvc.md) to retrieve the reference. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> <RestoreSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <VmRestoreSpec>     <PowerOnAfterRestore>false</PowerOnAfterRestore>     <HierarchyRootUid>urn:veeam:HierarchyRoot:1ed39e5b-06e1-4fbb-a106-52537b5e059e</HierarchyRootUid>     <QuickRollback>false</QuickRollback>     <VmRestoreParameters>       <VmRestorePointUid>urn:veeam:VmRestorePoint:af9396fb-99e6-4e94-a82a-914cc5a3f810</VmRestorePointUid>       <VmNewName>VM-restored</VmNewName>       <DatastoreRef>urn:vCloud:Datastore:1ed39e5b-06e1-4fbb-a106-52537b5e059e.urn:vcloud:datastore:9cfafa2e-e57b-4bc5-9690-933947c62b80</DatastoreRef>       <OrgVdcStorageProfileRef>urn:vCloud:OrgVdcStorageProfile:1ed39e5b-06e1-4fbb-a106-52537b5e059e.urn:vcloud:vdcstorageprofile:7e7ffe3a-33fa-4f9e-805b-c08b1a3645bf</OrgVdcStorageProfileRef>       <LinkedCloneVmTemplateRef/>     </VmRestoreParameters>   </VmRestoreSpec> </RestoreSpec> |

JSON Representation

|  |
| --- |
| {   "VmRestoreSpec": {     "PowerOnAfterRestore": false,     "HierarchyRootUid": "urn:veeam:HierarchyRoot:1ed39e5b-06e1-4fbb-a106-52537b5e059e",     "QuickRollback": false,     "VmRestoreParameters": {       "VmRestorePointUid": "urn:veeam:VmRestorePoint:af9396fb-99e6-4e94-a82a-914cc5a3f810",       "VmNewName": "VM-restored",       "DatastoreRef": "urn:vCloud:Datastore:1ed39e5b-06e1-4fbb-a106-52537b5e059e.urn:vcloud:datastore:9cfafa2e-e57b-4bc5-9690-933947c62b80",       "OrgVdcStorageProfileRef": "urn:vCloud:OrgVdcStorageProfile:1ed39e5b-06e1-4fbb-a106-52537b5e059e.urn:vcloud:vdcstorageprofile:7e7ffe3a-33fa-4f9e-805b-c08b1a  3645bf",       "LinkedCloneVmTemplateRef": ""     }   }  } |

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

The example below restores a VM from the restore point having ID b32c22c4-79af-4486-b2e2-1a3897db5c61:

|  |
| --- |
| Request:  POST https://localhost:9398/api/vmRestorePoints/b32c22c4-79af-4486-b2e2-1a3897db5c61?action=restore    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <RestoreSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <VmRestoreSpec>     <PowerOnAfterRestore>false</PowerOnAfterRestore>     <QuickRollback>false</QuickRollback>     <KeepOriginalVM>true</KeepOriginalVM>   </VmRestoreSpec> </RestoreSpec>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>StartVMRestore</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />     <Link Rel="Related" Type="RestoreSession" Href="https://localhost:9398/api/restoreSessions/d67d532a-9ce2-43b8-88c6-90354f2f8727?format=Entity" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>StartVMRestore</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
