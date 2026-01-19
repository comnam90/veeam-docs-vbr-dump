---
title: "PUT /cloud/hardwarePlans/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/put_hardwareplans_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# PUT /cloud/hardwarePlans/{ID}


Edits settings of a hardware plan with the specified ID.

Request

To edit settings of the hardware plan, send the PUT HTTP request to the /cloud/hardwarePlans/{ID} resource.

HTTP Request

|  |
| --- |
| PUT https://<Enterprise-Manager>:9398/api/cloud/hardwarePlans/{ID} |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters for the hardware plan whose settings must be updated. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Description | String | Description for the hardware plan. | Yes | 0/1 |
| ProcessorUsageLimitMhz | Int | Limit of CPU that can be used by all VM replicas of the tenant subscribed to the hardware plan.  To let the replicas use all available CPU resources, set the value to -1. | Yes | 1/1 |
| MemoryUsageLimitMb | Int | Limit of RAM that can be used by all VM replicas of the tenant subscribed to the hardware plan.  To let the replicas use all available RAM resources, set the value to -1. | Yes | 1/1 |
| HardwarePlanDetails | ViCloudHardwarePlan or HvCloudHardwarePlan | Parameters for the hardware plan. For details on parameters for VMware hardware plans, see [VMware Hardware Plan Settings](post_hardwareplans.md#vmware). For details on parameters for Hyper-V hardware plans, see [Hyper-V Hardware Plan Settings](post_hardwareplans.md#hyperv). | Yes | 1/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "Description": "Hardware Plan for VMware",   "ProcessorUsageLimitMhz": 10000,   "MemoryUsageLimitMb": 20000,   "HardwarePlanDetails": {     "ViCloudHardwarePlan": {       "HypervisorHostRef": "urn:VMware:Host:b7f17482-2f34-446c-976c-924539a98b0b.host-438",       "ParentType": "HostSystem",       "ParentName": "esx01.tech.local",       "Datastores": {         "Datastores": [           {             "FriendlyName": "Cloud Replicas",             "DatastoreType": "Datastore",             "Reference": "urn:VMware:Datastore:e8c0a941-cda3-488d-8a41-b53d747f3a92.datastore-441",             "RootPath": "",             "QuotaGb": 500,             "Id": "5df6b488-3a56-4dde-88d2-5e1c93280395"           }         ]       }     }   },   "Name": "VMware",   "UID": "urn:veeam:CloudHardwarePlan:e8c0a941-cda3-488d-8a41-b53d747f3a92",   "Href": "https://localhost:9398/api/cloud/hardwarePlans/e8c0a941-cda3-488d-8a41-b53d747f3a92?format\u003dEntity",   "Type": "CloudHardwarePlan"  } |

|  |
| --- |
| Note |
| You cannot change the number of networks in the hardware plan when editing hardware plan settings. |

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

The example below updates the description and datastore quota settings for the hardware plan with ID e8c0a941-cda3-488d-8a41-b53d747f3a92.

|  |
| --- |
| Request:  PUT https://localhost:9398/api/cloud/hardwarePlans/e8c0a941-cda3-488d-8a41-b53d747f3a92    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <CloudHardwarePlan Type="CloudHardwarePlan" Href="https://localhost:9398/api/cloud/hardwarePlans/e8c0a941-cda3-488d-8a41-b53d747f3a92?format=Entity" Name="VMware" UID="urn:veeam:CloudHardwarePlan:e8c0a941-cda3-488d-8a41-b53d747f3a92" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <Description>Hardware Plan for VMware VMs Replication</Description>   <ProcessorUsageLimitMhz>10000</ProcessorUsageLimitMhz>   <MemoryUsageLimitMb>20000</MemoryUsageLimitMb>   <HardwarePlanDetails>     <ViCloudHardwarePlan>       <HypervisorHostRef>urn:VMware:Host:b7f17482-2f34-446c-976c-924539a98b0b.host-438</HypervisorHostRef>       <ParentType>HostSystem</ParentType>       <ParentName>esx01.tech.local</ParentName>       <Datastores>         <Datastore Id="5df6b488-3a56-4dde-88d2-5e1c93280395">           <FriendlyName>Cloud Replicas</FriendlyName>           <DatastoreType>Datastore</DatastoreType>           <Reference>urn:VMware:Datastore:e8c0a941-cda3-488d-8a41-b53d747f3a92.datastore-441</Reference>           <RootPath/>           <QuotaGb>700</QuotaGb>         </Datastore>       </Datastores>     </ViCloudHardwarePlan>   </HardwarePlanDetails> </CloudHardwarePlan>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>EditCloudHardwarePlan</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>EditCloudHardwarePlan</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |


