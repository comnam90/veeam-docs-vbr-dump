---
title: "POST /selfService/vSphere/Configs"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_selfservice_vsphere_configs.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# POST /selfService/vSphere/Configs


Creates a vSphere Self-Service Backup Portal tenant access configuration.

Request

To create a vSphere Self-Service Backup Portal tenant access configuration, send the POST HTTP request to the /selfService/vSphere/Configs resource.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/selfService/vSphere/Configs |

Request Header

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters of the vSphere Self-Service Backup Portal tenant access configuration. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body contains the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| AccountName | String | Name of the user or group account for which the tenant access configuration is created. The account must be created in advance on a vCenter Server processed by a backup server added to Veeam Backup Enterprise Manager. | Yes | 1/1 |
| AccountType | String | Type of the tenant access configuration. Possible values:   * User — tenant access configuration is created for a vSphere user. * Group — tenant access configuration is created for a vSphere group. | False | 0/1 |
| RepositoryUid | UidType | UID of the backup repository on which the storage quota for the tenant of vSphere Self-Service Backup Portal must be created, for example: urn:veeam:Repository:893d2ecc-879a-4f2a-8a31-3594t7cr1ya4.  You cannot assign to tenants quotas on cloud repositories, as well as NetApp or Nimble storage systems that store snapshots created by [Veeam snapshot-only jobs](https://helpcenter.veeam.com/docs/backup/vsphere/snapshot_only_job_perform.html?ver=120). | Yes | 1/1 |
| QuotaGb | Long | Size of the storage quota assigned to the tenant (in GB). | Yes | 1/1 |
| PerUser | Boolean | Defines whether users of the group for which the tenant access configuration is created will have separate quotas on the backup repository and what backup jobs will be available to users. Possible values:   * True — each user of the group has a separate quota on the backup repository. Each user has access to backup jobs created by this user only. * False — all users of the group share the same quota on the backup repository. Each user has access to all backup jobs created by users of the group. | Yes | 0/1 |
| TemplateJobUid | UidType | UID of the backup job that will be used as a template for backup jobs created by the tenant of vSphere Self-Service Backup Portal. The backup job must be created in advance on the backup server connected to Veeam Backup Enterprise Manager.  Settings of the specified job will be applied to backup jobs created by the tenant. If the job ID is not specified, tenant jobs will be configured with the default vSphere backup job settings.  Settings applied to backup jobs of the tenant will be displayed in the representation of the [/selfService/vSphere/Configs/{ID}/backupJobSettings](selfservice_vsphere_configs_id_backupsettings.md) resource. | Yes | 0/1 |
| JobSchedulerType | String | Job scheduling options. Possible values:   * Full — tenant of the vSphere Self-Service Backup Portal has full access to all job scheduling options. * Partial — tenant of the vSphere Self-Service Backup Portal can create daily and monthly jobs only. * Random — tenant of the vSphere Self-Service Backup Portal can create daily jobs with randomized start time within the backup window. * Disabled — tenant of the vSphere Self-Service Backup Portal can create only jobs with no schedule assigned. | Yes | 0/1 |
| HighPriorityJob | Boolean | Defines whether the backup job has a high priority. Possible values:   * True * False | Yes | 0/1 |
| VCentersScope | VCentersScopeListType | Defines a list of vCenter Servers whose VMs are available to the tenant. By default, the tenant has access to all vCenter Servers. For details, see [vCenters Scope Settings](#vCenters). | Yes | 0/1 |
| Tags | TagsListType | vSphere tags that define what VMs will be available to the tenant. For details, see [vSphere Tags](#tags).  vSphere tags must be specified if the vSphere tags delegation mode is selected in Veeam Backup Enterprise Manager. | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "AccountName": "Administrators",   "RepositoryUid": "urn:veeam:Repository:425b6739-5082-4f7a-99fb-1ae13ef87d9f",   "QuotaGb": 500,   "PerUser": false,   "TemplateJobUid": "urn:veeam:Job:24f70e27-549a-4126-bfe5-167cca158a0f",   "JobSchedulerType": "Full",   "HighPriorityJob": true,   "VCentersScopes": [     "urn:veeam:ManagedServer:6edb23da-560b-4759-951f-1da6aca08169",     "urn:veeam:ManagedServer:095585e0-6a9a-4bb8-8433-a1d815687ce9"   ],   "Tags": [     "RestAPITag"   ]  } |

vCenters Scope Settings

You can define a list of vCenter Servers whose VMs are available to the tenant. By default, the tenant has access to all vCenter Servers.

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| VCenterUid | UidType | UID of the vCenter Server  that must be available to the tenant, for example: urn:veeam:ManagedServer:6edb23da-560b-4759-951f-1da6aca08169. | Yes | 0/- |

For example:

XML Representation

|  |
| --- |
| <VCentersScope>   <VCenterUid>urn:veeam:ManagedServer:6edb23da-560b-4759-951f-1da6aca08169</VCenterUid>   <VCenterUid>urn:veeam:ManagedServer:095585e0-6a9a-4bb8-8433-a1d815687ce9</VCenterUid> </VCentersScope> |

JSON Representation

|  |
| --- |
| "VCentersScope": [  "urn:veeam:ManagedServer:6edb23da-560b-4759-951f-1da6aca08169",  "urn:veeam:ManagedServer:095585e0-6a9a-4bb8-8433-a1d815687ce9"  ] |

vSphere Tags

If the vSphere tags delegation mode is selected in Veeam Backup Enterprise Manager, you must specify tags in the tenant access configuration. The tenant will be able to back up only those VMs to which the specified tags are assigned.

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Tag | String | vSphere tag assigned to a VM that must be available to the tenant. | Yes | 0/- |

For example:

|  |
| --- |
| <Tags>   <Tag>RestAPITag</Tag> </Tags> |

JSON Representation

|  |
| --- |
| "Tags": [  "RestAPITag"  ] |

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

None.

Example

The example below creates a new tenant access configuration for the vSphere user with the name tech\william.fox. The storage quota of 100 GB is created on the backup repository that has ID df9903aa-d2b6-4edd-9a0b-057bc8dd4451. The backup job with ID 24f70e27-549a-4126-bfe5-167cca158a0f is used as a template for backup jobs created by the tenant of the vSphere Self-Service Backup Portal. The tenant has full access to all job scheduling options.

|  |
| --- |
| Request:  POST https://localhost:9398/api/selfService/vSphere/Configs    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <VSphereSelfServiceCreateSpec xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <AccountName>tech\william.fox</AccountName>   <RepositoryUid>urn:veeam:Repository:df9903aa-d2b6-4edd-9a0b-057bc8dd4451</RepositoryUid>   <QuotaGb>100</QuotaGb>   <PerUser>false</PerUser>   <TemplateJobUid>urn:veeam:Job:24f70e27-549a-4126-bfe5-167cca158a0f</TemplateJobUid>   <TemplateMode>Default</TemplateMode>   <JobSchedulerType>Full</JobSchedulerType>   <Tags>     <Tag>RestAPITag</Tag>   </Tags> </VSphereSelfServiceCreateSpec>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>CreateVSphereSelfServiceConfig</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" Href="https://localhost:9398/api/tasks/task-1" Type="Task">   <Links>     <Link Href="https://localhost:9398/api/tasks/task-1" Rel="Delete"/>     <Link Href="https://localhost:9398/api/selfService/vSphere/Configs/9525996c-2e11-4ece-9d0b-41d4fda59fd7" Name="tech\william.fox" Type="VSphereSelfServiceConfigReference" Rel="Related"/>   </Links>   <TaskId>task-311</TaskId>   <State>Finished</State>   <Operation>CreateVSphereSelfServiceConfig</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |


