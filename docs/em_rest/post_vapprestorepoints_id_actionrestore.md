---
title: "post_vapprestorepoints_id_actionrestore"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_vapprestorepoints_id_actionrestore.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Starts the entire VM restore process from the vApp restore point having the specified ID.

Supported Platforms

The request is supported for the VMware Cloud Director platform.

Request

To start the full vApp restore, send the POST HTTP request to the /vAppRestorePoints/{ID}/?actions=restore URL.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/vAppRestorepoints/{ID}?action=restore |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send the parameters for the full vApp restore process. The body of the request must conform to the  [XML Schema Definitionem\_rest\_](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| PowerOnAfter | Boolean | Specifies if VMs in the vApp must be powered on after the restore process is complete. | Yes | 1/1 |
| HierarchyRoot | UidType | UID of the host on which the vApp must be restored, for example: urn:veeam:HierarchyRoot:2dcfebc9-eb06-4d3b-a639-c1cfa8483621. | Yes | 1/1 |
| OrgVdcRef | HierarchyObj Ref | Reference to the OrgVdc to which the vApp must be restored. The reference can be [constructed manually](constructing_hierarchyobjreftype.md) or obtained with the lookup service. For details on using the lookup, see [Virtual Infrastructure Lookup](lookup_service.md). | Yes | 1/1 |
| vAppNewName | String | Name of the restored vApp. If this parameter is not specified, the initial vApp name will be used. | Yes | 0/1 |
| VmsRestore Parameters | vCloudVmRestoreParametersInfo | Defines [VM-specific parameters](post_vmrestorepoints_id_actionrestore.md#params). | No | — |

VM Restore Parameters

VM restore parameters are provided in the following format:

XML Representation

|  |
| --- |
| <VmsRestoreParameters>   <Vm>     <VmRestorePointUid>urn:veeam:VmRestorePoint:48c8cd65-d5fa-4ca6-8a98-d3fde641086e</VmRestorePointUid>     <VmNewName>VM1</VmNewName>     <DatastoreRef>urn:vCloud:Datastore:fa099d3b-7376-49b1-884c-bb6fa47c7b1e.urn:vcloud:datastore:68d9f62d-f3c1-4842-8ad6-9b7faca3c92a</DatastoreRef>     <OrgVdcStorageProfileRef>urn:vCloud:OrgVdcStorageProfile:fa099d3b-7376-49b1-884c-bb6fa47c7b1e.urn:vcloud:vdcstorageprofile:1afeb3cc-bc4f-4e0f-b092-a3f8bbe70adc</OrgVdcStorageProfileRef>     <LinkedCloneVmTemplateRef/>   </Vm> </VmsRestoreParameters> |

JSON Representation

|  |
| --- |
| "VmsRestoreParameters": {   "Vm": {     "VmRestorePointUid": "urn:veeam:VmRestorePoint:48c8cd65-d5fa-4ca6-8a98-d3fde641086e",     "VmNewName": "VM1",     "DatastoreRef": "urn:vCloud:Datastore:fa099d3b-7376-49b1-884c-bb6fa47c7b1e.urn:vcloud:datastore:68d9f62d-f3c1-4842-8ad6-9b7faca3c92a",     "OrgVdcStorageProfileRef": "urn:vCloud:OrgVdcStorageProfile:fa099d3b-7376-49b1-884c-bb6fa47c7b1e.urn:vcloud:vdcstorageprofile:1afeb3cc-bc4f-4e0f-b092-a3f8bbe70adc",     "LinkedCloneVmTemplateRef": ""   }  } |

You can define the following restore parameters for VMs:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| VmRestorePointUid | UidType | UID of the restore point from which the VM must be restored, for example: urn:veeam:VmRestorePoint:48c8cd65-d5fa-4ca6-8a98-d3fde641086e. | Yes | 1/1 |
| VmNewName | String | Name of the restored VM. If this parameter is not specified, the VM is restored with its initial name. | Yes | 0/1 |
| DatastoreRef | HierarchyObjRefType | Reference to the datastore on which VM files must be placed. You can [construct the reference manually](constructing_hierarchyobjreftype.md) or use the [lookup service](lookupsvc.md) to retrieve the reference. | Yes | 0/1 |
| OrgVdcStorageProfileRef | HierarchyObjRefType | Reference to the OrgVdc profile to be used for the restored VM. You can [construct the reference manually](constructing_hierarchyobjreftype.md) or use the [lookup service](lookupsvc.md) to retrieve the reference. | Yes | 0/1 |
| LinkedCloneVmTemplateRef | HierarchyObjRefType | (For linked clone VMs) Reference to the template that was used to create the VM. You can [construct the reference manually](constructing_hierarchyobjreftype.md) or use the [lookup service](lookupsvc.md) to retrieve the reference. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> <RestoreSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <vCloudVAppRestoreSpec>     <PowerOnAfterRestore>false</PowerOnAfterRestore>     <HierarchyRootUid>urn:veeam:HierarchyRoot:2dcfebc9-eb06-4d3b-a639-c1cfa8483621</HierarchyRootUid>     <OrgVdcRef>urn:vCloud:OrgVdc:2dcfebc9-eb06-4d3b-a639-c1cfa8483621.urn:vcloud:vdc:1d0bf8ae-8eac-4772-b675-5a4cf06fcbc1</OrgVdcRef>     <vAppNewName>vApp2</vAppNewName>     <VmsRestoreParameters>       <Vm>         <VmRestorePointUid>urn:veeam:VmRestorePoint:b3755195-80bc-4149-937b-4d58d6caac34</VmRestorePointUid>         <VmNewName>VM1</VmNewName>         <DatastoreRef>urn:vCloud:Datastore:2dcfebc9-eb06-4d3b-a639-c1cfa8483621.urn:vcloud:datastore:68d9f62d-f3c1-4842-8ad6-9b7faca3c92a</DatastoreRef>         <OrgVdcStorageProfileRef>urn:vCloud:OrgVdcStorageProfile:2dcfebc9-eb06-4d3b-a639-c1cfa8483621.urn:vcloud:vdcstorageprofile:1afeb3cc-bc4f-4e0f-b092-a3f8bbe70adc</OrgVdcStorageProfileRef>         <LinkedCloneVmTemplateRef/>       </Vm>       <Vm>         <VmRestorePointUid>urn:veeam:VmRestorePoint:3acc4a1d-8a11-4119-b361-291e2d785dde</VmRestorePointUid>         <VmNewName>VM2</VmNewName>         <DatastoreRef>urn:vCloud:Datastore:2dcfebc9-eb06-4d3b-a639-c1cfa8483621.urn:vcloud:datastore:68d9f62d-f3c1-4842-8ad6-9b7faca3c92a</DatastoreRef>         <OrgVdcStorageProfileRef>urn:vCloud:OrgVdcStorageProfile:2dcfebc9-eb06-4d3b-a639-c1cfa8483621.urn:vcloud:vdcstorageprofile:1afeb3cc-bc4f-4e0f-b092-a3f8bbe70adc</OrgVdcStorageProfileRef>         <LinkedCloneVmTemplateRef/>       </Vm>     </VmsRestoreParameters>   </vCloudVAppRestoreSpec> </RestoreSpec> |

JSON Representation

|  |
| --- |
| {   "VCloudVAppRestoreSpec": {     "PowerOnAfterRestore": false,     "HierarchyRootUid": "urn:veeam:HierarchyRoot:2dcfebc9-eb06-4d3b-a639-c1cfa8483621",     "OrgVdcRef": "urn:vCloud:OrgVdc:2dcfebc9-eb06-4d3b-a639-c1cfa8483621.urn:vcloud:vdc:1d0bf8ae-8eac-4772-b675-5a4cf06fcbc1",     "VAppNewName": "vApp2",     "VmsRestoreParameters": [       {         "VmRestorePointUid": "urn:veeam:VmRestorePoint:b3755195-80bc-4149-937b-4d58d6caac34",         "VmNewName": "VM1",         "DatastoreRef": "urn:vCloud:Datastore:2dcfebc9-eb06-4d3b-a639-c1cfa8483621.urn:vcloud:datastore:68d9f62d-f3c1-4842-8ad6-9b7faca3c92a",         "OrgVdcStorageProfileRef": "urn:vCloud:OrgVdcStorageProfile:2dcfebc9-eb06-4d3b-a639-c1cfa8483621.urn:vcloud:vdcstorageprofile:1afeb3cc-bc4f-4e0f-b092-a3f8  bbe70adc",         "LinkedCloneVmTemplateRef": ""       },       {         "VmRestorePointUid": "urn:veeam:VmRestorePoint:3acc4a1d-8a11-4119-b361-291e2d785dde",         "VmNewName": "VM2",         "DatastoreRef": "urn:vCloud:Datastore:2dcfebc9-eb06-4d3b-a639-c1cfa8483621.urn:vcloud:datastore:68d9f62d-f3c1-4842-8ad6-9b7faca3c92a",         "OrgVdcStorageProfileRef": "urn:vCloud:OrgVdcStorageProfile:2dcfebc9-eb06-4d3b-a639-c1cfa8483621.urn:vcloud:vdcstorageprofile:1afeb3cc-bc4f-4e0f-b092-a3f8  bbe70adc",         "LinkedCloneVmTemplateRef": ""       }     ]   }  } |

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

The example below restores vApp2 from the restore point having ID f139af13-0d49-49c1-bf88-8b2d0db621e3 and registers it on the same host under a new name — vApp2\_restored.

|  |
| --- |
| Request:  POST https://localhost:9398/api/vAppRestorePoints/f139af13-0d49-49c1-bf88-8b2d0db621e3?action=restore    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <RestoreSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <vCloudVAppRestoreSpec>     <PowerOnAfterRestore>false</PowerOnAfterRestore>     <HierarchyRootUid>urn:veeam:HierarchyRoot:2dcfebc9-eb06-4d3b-a639-c1cfa8483621</HierarchyRootUid>     <OrgVdcRef>urn:vCloud:OrgVdc:2dcfebc9-eb06-4d3b-a639-c1cfa8483621.urn:vcloud:vdc:1d0bf8ae-8eac-4772-b675-5a4cf06fcbc1</OrgVdcRef>     <vAppNewName>vApp2\_restored</vAppNewName>   </vCloudVAppRestoreSpec> </RestoreSpec>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>StartvAppRestore</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />     <Link Rel="Related" Type="RestoreSession" Href="https://localhost:9398/api/restoreSessions/d67d532a-9ce2-43b8-88c6-90354f2f8727?format=Entity" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>StartvAppRestore</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
