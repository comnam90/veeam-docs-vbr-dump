---
title: "post_vcloud_orgconfigs"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/post_vcloud_orgconfigs.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Creates a VMware Cloud Director organization configuration.

Request

To create a VMware Cloud Director organization configuration, send the POST HTTP request to the /vCloud/orgConfigs resource.

HTTP Request

|  |
| --- |
| POST https://<Enterprise-Manager>:9398/api/vCloud/orgConfigs |

Request Header

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters of the VMware Cloud Director organization configuration. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| OrganizationName | String | Name of the VMware Cloud Director organization for which the configuration is created. The VMware Cloud Director organization must be created in advance on a VMware Cloud Director server processed by a backup server added to Veeam Backup Enterprise Manager. | Yes | 1/1 |
| BackupServerUid | UidType | UID of the backup server that must process VMs of the VMware Cloud Director organization, for example: urn:veeam:BackupServer:1cf4ea89-89d9-4b4e-a285-71bd8c705222. | Yes | 1/1 |
| RepositoryUid | UidType | UID of the backup repository on which the storage quota for the VMware Cloud Director organization must be created, for example: urn:veeam:Repository:82db96c3-445c-4a7e-9587-f2d523e839f4. | Yes | 1/1 |
| QuotaGb | Long | Size of the storage quota assigned to the VMware Cloud Director organization (in GB). | Yes | 1/1 |
| TemplateJobUid | UidType | UID of the VMware Cloud Director backup job that will be used as a template for VMware Cloud Director organization VMs processing. The backup job must be created in advance on the backup server connected to Veeam Backup Enterprise Manager.  Settings of the specified job will be applied to backup jobs created by tenant-side users. If the job UID is not specified, tenant-side jobs will be configured with the default VMware Cloud Director backup job settings.  Job settings applied to backup jobs for the VMware Cloud Director organization will be listed in the representation of the [/vCloud/orgConfigs/{ID}/backupJobSettings](vcloud_orgconfigs_id_backupjobsettings.md) resource. | Yes | 0/1 |
| JobSchedulerType | String | Job scheduling options. Possible values:   * Full — VMware Cloud Director organization members have full access to all job scheduling options. * Partial — VMware Cloud Director organization members can create daily and monthly jobs only. * Random — VMware Cloud Director organization members can create daily jobs with randomized start time within the backup window. * Disabled — VMware Cloud Director organization members can create only jobs with no schedule assigned. | Yes | 1/1 |
| HighPriorityJob | Boolean | Defines whether the backup job has a high priority. Possible values:   * True * False | Yes | 0/1 |
| HostUid | UidType | UID of the VMware Cloud Director host where the VMware Cloud Director organization has been created. | Yes | 1/1 |
| RepositoryFriendlyName | String | Backup repository name displayed to VMware Cloud Director organization members, for example: Backup Repository 1. | Yes | 1/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "OrganizationName": "organization02",   "BackupServerUid": "urn:veeam:BackupServer:7445e6ce-86f5-4171-b909-dac209c66563",   "RepositoryUid": "urn:veeam:Repository:425b6739-5082-4f7a-99fb-1ae13ef87d9f",   "QuotaGb": 100,   "RepositoryFriendlyName": "Backup Repository 1",   "TemplateJobUid": "urn:veeam:Job:1406b437-e4eb-470f-876a-60dc2b83728f",   "JobSchedulerType": "Full",   "HighPriorityJob": false,   "HostUid": "urn:veeam:ManagedServer:bd8e5927-9406-4019-85a5-ef90d314a8c7"  } |

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

The example below creates a new configuration for the VMware Cloud Director organization with the name organization02 with the following parameters:

* Storage quota: 500 GB
* Backup repository ID: 425b6739-5082-4f7a-99fb-1ae13ef87d9f
* Backup repository name displayed to tenant-side users: Backup Repository 1

The backup job with ID 1406b437-e4eb-470f-876a-60dc2b83728f is used as a template for tenant-side backup jobs. VMware Cloud Director organization members have full access to all job scheduling options.

|  |
| --- |
| Request:  POST https://localhost:9398/api/vCloud/orgConfigs    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <VCloudOrganizationConfigCreateSpec xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0">   <OrganizationName>organization02</OrganizationName>   <BackupServerUid>urn:veeam:BackupServer:7445e6ce-86f5-4171-b909-dac209c66563</BackupServerUid>   <RepositoryUid>urn:veeam:Repository:425b6739-5082-4f7a-99fb-1ae13ef87d9f</RepositoryUid>   <QuotaGb>500</QuotaGb>   <TemplateJobUid>urn:veeam:Job:1406b437-e4eb-470f-876a-60dc2b83728f</TemplateJobUid>   <JobSchedulerType>Full</JobSchedulerType>   <HighPriorityJob>false</HighPriorityJob>   <HostUid>urn:veeam:ManagedServer:bd8e5927-9406-4019-85a5-ef90d314a8c7</HostUid>   <RepositoryFriendlyName>Backup Repository 1</RepositoryFriendlyName> </VCloudOrganizationConfigCreateSpec>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>CreateVCloudOrganizationConfig</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />     <Link Rel="Related" Type="VCloudOrganizationConfigReference" Href="https://localhost:9398/api/vCloud/orgConfigs/ee1018b4-6f52-489e-80b7-8005e0b2d640" Name="org01" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>CreateVCloudOrganizationConfig</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
