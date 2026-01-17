---
title: "POST /cloud/hardwarePlans"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_hardwareplans.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Configures a new hardware plan on the backup server connected to Veeam Backup Enterprise Manager.

Request

To create a new hardware plan, send the POST HTTP request to the /cloud/hardwarePlans resource.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/cloud/hardwarePlans |

Request Header

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters for the new hardware plan. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| BackupServerUid | String | UID of the backup server on which the hardware plan must be created. | Yes | 1/1 |
| Name | String | Name for the hardware plan, for example: VMware Hardware Plan. | Yes | 1/1 |
| Description | String | Description for the hardware plan. | Yes | 0/1 |
| ProcessorUsageLimitMhz | Int | Limit of CPU that can be used by all VM replicas of the tenant subscribed to the hardware plan.  To let the replicas use all available CPU resources, set the value to -1. | Yes | 1/1 |
| MemoryUsageLimitMb | Int | Limit of RAM that can be used by all VM replicas of the tenant subscribed to the hardware plan.  To let the replicas use all available RAM resources, set the value to -1. | Yes | 1/1 |
| HardwarePlanDetails | ViCloudHardwarePlan or HvCloudHardwarePlan | Parameters for the created hardware plan. For details on creating a VMware hardware plan, see [VMware Hardware Plan Settings](post_hardwareplans.md#vmware). For details on creating a Hyper-V hardware plan, see [Hyper-V Hardware Plan Settings](post_hardwareplans.md#hyperv). | Yes | 1/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "BackupServerUid": "urn:veeam:BackupServer:8fff3b8e-c3f1-4ef5-aecc-561f07bf9982",   "Name": "VMware Gold",   "Description": "Hardware Plan for VMware",   "ProcessorUsageLimitMhz": 10000,   "MemoryUsageLimitMb": 20000,   "HardwarePlanDetails": {     "ViCloudHardwarePlan": {       "HypervisorHostRef": "urn:VMware:Host:b7f17482-2f34-446c-976c-924539a98b0b.host-438",       "ParentType": "HostSystem",       "ParentName": "esx01.tech.local",       "Datastores": {         "Datastores": [           {             "FriendlyName": "Cloud Replicas",             "DatastoreType": "Datastore",             "Reference": "urn:VMware:Datastore:ed6ad5f1-671b-4875-9d81-72a431953aca.datastore-441",             "QuotaGb": 500           }         ]       },       "Network": {         "CountWithInternet": 1,         "CountWithoutInternet": 0       }     }   }  } |

VMware Hardware Plan Settings

You can define the following parameters for the VMware hardware plan:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| HypervisorHostRef | HierarchyObjRefType | Reference to the virtualization host on which tenant VM replicas should be registered, for example: urn:VMware:Host:b7f17482-2f34-446c-976c-924539a98b0b.host-438. | Yes | 1/1 |
| ParentType | String | Type of the VMware object. Possible values:   * ClusterComputeResource * HostSystem | Yes | 1/1 |
| ParentName | String | Name of the host or cluster. | Yes | 1/1 |
| Datastores | ViCloudHardwarePlanDatastoreInfoListType | Datastore parameters for the created hardware plan. For details, see [Datastore Settings](post_hardwareplans.md#datastore). | Yes | 1/1 |
| Network | CloudHardwarePlanNetworkInfo | Network parameters for the created hardware plan. For details, see [Network Settings](post_hardwareplans.md#network). | Yes | 0/1 |

|  |
| --- |
| Note |
| VMware hardware plan settings must be defined in the ViCloudHardwarePlan section of the request body. |

For example:

XML Representation

|  |
| --- |
| <ViCloudHardwarePlan>   <HypervisorHostRef>urn:VMware:Host:b7f17482-2f34-446c-976c-924539a98b0b.host-438</HypervisorHostRef>   <ParentType>HostSystem</ParentType>   <ParentName>esx01.tech.local</ParentName>   <Datastores>     <Datastore>       <FriendlyName>Cloud Replicas</FriendlyName>       <DatastoreType>Datastore</DatastoreType>       <Reference>urn:VMware:Datastore:ed6ad5f1-671b-4875-9d81-72a431953aca.datastore-441</Reference>       <QuotaGb>500</QuotaGb>     </Datastore>   </Datastores>   <Network>     <CountWithInternet>1</CountWithInternet>     <CountWithoutInternet>0</CountWithoutInternet>   </Network> </ViCloudHardwarePlan> |

JSON Representation

|  |
| --- |
| "ViCloudHardwarePlan": {   "HypervisorHostRef": "urn:VMware:Host:b7f17482-2f34-446c-976c-924539a98b0b.host-438",   "ParentType": "HostSystem",   "ParentName": "esx01.tech.local",   "Datastores": {     "Datastores": [       {         "FriendlyName": "Cloud Replicas",         "DatastoreType": "Datastore",         "Reference": "urn:VMware:Datastore:ed6ad5f1-671b-4875-9d81-72a431953aca.datastore-441",         "QuotaGb": 500       }     ]   },   "Network": {     "CountWithInternet": 1,     "CountWithoutInternet": 0   }  } |

Datastore Settings

You can define the following datastore parameters for the VMware hardware plan:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| FriendlyName | String | Name of the datastore as displayed to the tenant, for example: Cloud Replicas. | Yes | 1/1 |
| DatastoreType | String | Type of the datastore. Possible values:   * Datastore * StoragePod | Yes | 1/1 |
| Reference | HierarchyObjRefType | Reference to the datastore on which tenant VM replicas should be stored, for example: urn:VMware:Datastore:ed6ad5f1-671b-4875-9d81-72a431953aca.datastore-441. You can [construct the reference manually](constructing_hierarchyobjreftype.md) or use the [lookup service](lookupsvc.md) to retrieve the reference. | Yes | 1/1 |
| QuotaGb | Int | Storage quota for tenant VM replicas on the datastore (in GB). | Yes | 1/1 |

For example:

XML Representation

|  |
| --- |
| <Datastores>   <Datastore>     <FriendlyName>Cloud Replicas</FriendlyName>     <DatastoreType>Datastore</DatastoreType>     <Reference>urn:VMware:Datastore:ed6ad5f1-671b-4875-9d81-72a431953aca.datastore-441</Reference>     <QuotaGb>500</QuotaGb>   </Datastore> </Datastores> |

JSON Representation

|  |
| --- |
| "Datastores": {   "Datastores": [     {       "FriendlyName": "Cloud Replicas",       "DatastoreType": "Datastore",       "Reference": "urn:VMware:Datastore:ed6ad5f1-671b-4875-9d81-72a431953aca.datastore-441",       "QuotaGb": 500     }   ]  } |

Hyper-V Hardware Plan Settings

You can define the following parameters for the for the Hyper-V hardware plan:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| HypervisorHostRef | HierarchyObjRefType | Reference to the virtualization host on which tenant VM replicas should be registered, for example: urn:HyperV:Host:849a937a-3416-4f03-8111-67b06393afcb. You can [construct the reference manually](constructing_hierarchyobjreftype.md) or use the [lookup service](lookupsvc.md) to retrieve the reference. | Yes | 1/1 |
| Volumes | HvCloudHardwarePlanVolumesInfoListType | Storage volume parameters for the created hardware plan. For details, see [Volume Settings](post_hardwareplans.md#volume). | Yes | 1/1 |
| Network | CloudHardwarePlanNetworkInfo | Network parameters for the created hardware plan. For details, see [Network Settings](post_hardwareplans.md#network). | Yes | 0/1 |

|  |
| --- |
| Note |
| Hyper-V hardware plan settings must be defined in the HvCloudHardwarePlan section of the request body. |

For example:

XML Representation

|  |
| --- |
| <HvCloudHardwarePlan>   <HypervisorHostRef>urn:HyperV:Host:849a937a-3416-4f03-8111-67b06393afcb.</HypervisorHostRef>   <Volumes>     <Volume>       <FriendlyName>Cloud Replicas</FriendlyName>       <VolumePath>D:\Replicas</VolumePath>       <QuotaGb>300</QuotaGb>     </Volume>   </Volumes>   <Network>     <CountWithInternet>1</CountWithInternet>     <CountWithoutInternet>1</CountWithoutInternet>   </Network> </HvCloudHardwarePlan> |

JSON Representation

|  |
| --- |
| "HvCloudHardwarePlan": {   "HypervisorHostRef": "urn:HyperV:Host:849a937a-3416-4f03-8111-67b06393afcb.",   "Volumes": {     "Volumes": [       {         "FriendlyName": "Cloud Replicas",         "VolumePath": "D:\\Replicas",         "QuotaGb": 300       }     ]   },   "Network": {     "CountWithInternet": 1,     "CountWithoutInternet": 1  }  } |

Volume Settings

You can define the following storage volume parameters for the Hyper-V hardware plan:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| FriendlyName | String | Name of the volume as displayed to the tenant, for example: Cloud Replicas. | Yes | 1/1 |
| VolumePath | String | Path to a folder on the volume in which tenant VM replica files should be stored. | Yes | 1/1 |
| QuotaGb | Int | Storage quota for tenant VM replicas on the volume (in GB). | Yes | 1/1 |

For example:

XML Representation

|  |
| --- |
| <Volumes>   <Volume Id="66d75e14-a35a-4dfe-a919-9b2a3bf87e4a">     <FriendlyName>Cloud Replicas</FriendlyName>     <VolumePath>D:\Replicas</VolumePath>      <QuotaGb>300</QuotaGb>   </Volume> </Volumes> |

JSON Representation

|  |
| --- |
| "Volumes": {   "Volumes": [     {       "FriendlyName": "Cloud Replicas",       "VolumePath": "D:\\Replicas",       "QuotaGb": 300     }   ]  } |

Network Settings

You can define the following network parameters for the VMware or Hyper-V hardware plan:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| CountWithInternet | Int | Number of networks with internet access that will be available to tenant VM replicas. | Yes | 0/1 |
| CountWithoutInternet | Int | Number of networks without internet access that will be available to tenant VM replicas. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <Network>   <CountWithInternet>1</CountWithInternet>   <CountWithoutInternet>1</CountWithoutInternet> </Network> |

JSON Representation

|  |
| --- |
| "Network": {   "CountWithInternet": 1,   "CountWithoutInternet": 1  } |

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

The example below creates a VMware hardware plan on the backup server with ID 8fff3b8e-c3f1-4ef5-aecc-561f07bf9982.

|  |
| --- |
| Request:  POST https://localhost:9398/api/cloud/hardwarePlans    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <CloudHardwarePlanCreateSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <BackupServerUid>urn:veeam:BackupServer:8fff3b8e-c3f1-4ef5-aecc-561f07bf9982</BackupServerUid>   <Name>VMware Gold</Name>   <Description>Hardware Plan for VMware</Description>   <ProcessorUsageLimitMhz>10000</ProcessorUsageLimitMhz>   <MemoryUsageLimitMb>20000</MemoryUsageLimitMb>   <HardwarePlanDetails>     <ViCloudHardwarePlan>       <HypervisorHostRef>urn:VMware:Host:b7f17482-2f34-446c-976c-924539a98b0b.host-438</HypervisorHostRef>       <ParentType>HostSystem</ParentType>       <ParentName>esx01.tech.local</ParentName>       <Datastores>         <Datastore>           <FriendlyName>Cloud Replicas</FriendlyName>           <DatastoreType>Datastore</DatastoreType>           <Reference>urn:VMware:Datastore:ed6ad5f1-671b-4875-9d81-72a431953aca.datastore-441</Reference>           <QuotaGb>500</QuotaGb>         </Datastore>       </Datastores>       <Network>         <CountWithInternet>1</CountWithInternet>         <CountWithoutInternet>0</CountWithoutInternet>       </Network>     </ViCloudHardwarePlan>   </HardwarePlanDetails> </CloudHardwarePlanCreateSpec>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>CreateCloudGateway</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />     <Link Rel="Related" Type="CloudGateway" Href="https://localhost:9398/api/cloud/gateways/917be225-6744-4777-8096-cbabaec55006?format=Entity" Name="" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>CreateCloudHardwarePlan</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
