---
title: "PUT /vCloud/orgConfigs/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/put_vcloud_orgconfigs_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# PUT /vCloud/orgConfigs/{ID}


Edits settings of a VMware Cloud Director organization configuration with the specified ID.

Request

To edit settings of the VMware Cloud Director organization configuration, send the PUT HTTP request to the /vCloud/orgConfigs/{ID} resource.

HTTP Request

|  |
| --- |
| PUT https://<Enterprise-Manager>:9398/api/vCloud/orgConfigs/{ID} |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters for the VMware Cloud Director organization configuration whose settings must be updated. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| BackupServerUid | UidType | UID of the backup server that must process VMs of the VMware Cloud Director organization, for example: urn:veeam:BackupServer:1cf4ea89-89d9-4b4e-a285-71bd8c705222. | Yes | 1/1 |
| RepositoryUid | UidType | UID of the backup repository on which the storage quota for the VMware Cloud Director organization must be created, for example: urn:veeam:Repository:82db96c3-445c-4a7e-9587-f2d523e839f4 | Yes | 1/1 |
| QuotaGb | Long | Size of the storage quota assigned to the VMware Cloud Director organization (in GB). | Yes | 1/1 |
| IsDisabled | UShort | Defines if the VMware Cloud Director organization configuration is in the disabled state. Possible values:   * True * False   If the True value is specified, the VMware Cloud Director organization will use default organization settings. Default settings are specified in the sample configuration with the name Other organizations. Settings specified for this configuration are also applied to all organizations for which individual configurations are not created. | Yes | 1/1 |
| JobSettings | VCloudOrganizationConfigBackupJobSettings | VMware Cloud Director backup job options set for the organization. For details, see [VMware Cloud Director Backup Job Settings](#job). | Yes | 1/1 |
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
| {   "BackupServerUid": "urn:veeam:BackupServer:1cf4ea89-89d9-4b4e-a285-71bd8c705222",   "RepositoryUid": "urn:veeam:Repository:df9903aa-d2b6-4edd-9a0b-057bc8dd4451",   "QuotaGb": 1024,   "IsDisabled": false,   "JobSettings": {     "DefaultSettings": true,     "JobSchedulerType": "Full",     "HighPriorityJob": false   },   "HostUid": "urn:veeam:ManagedServer:24a14898-77d0-4881-bbf8-c8ba71ce4d55",   "RepositoryFriendlyName": "Repository 1",   "Name": "org02",   "UID": "urn:veeam:VCloudOrganizationConfig:228fef7b-6e5e-4107-886e-40c8f482b5c7",   "Href": "https://localhost:9398/api/vCloud/orgConfigs/228fef7b-6e5e-4107-886e-40c8f482b5c7?format\u003dEntity",   "Type": "VCloudOrganizationConfig"  } |

VMware Cloud Director Backup Job Settings

You can define the following parameters for tenant-side VMware Cloud Director backup jobs:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| DefaultSettings | Bool | Defines whether tenant-side jobs created for the organization must be configured with the default VMware Cloud Director backup job settings. Possible values:   * True * False   If set to False, the UID of the backup job that will be used as a template for tenant-side jobs must be specified in the [CopyFromThisJob](#id) element. | Yes | 0/1 |
| CustomSettings | Bool | Defines whether tenant-side jobs created for the organization must use settings of a specific VMware Cloud Director backup job. Possible values:   * True * False   If set to True, the UID of the backup job that will be used as a template for tenant-side jobs must be specified in the [CopyFromThisJob](#id) element. | Yes | 0/1 |
| TemplateJobUid | UidType | UID of the VMware Cloud Director backup job that will be used as a template for VMware Cloud Director organization VMs processing. The backup job must be created in advance on the backup server connected to Veeam Backup Enterprise Manager. | Yes | 0/1 |
| JobSchedulerType | String | Job scheduling options. Possible values:   * Full — VMware Cloud Director organization members have full access to all job scheduling options. * Partial — VMware Cloud Director organization members can create daily and monthly jobs only. * Random — VMware Cloud Director organization members can create daily jobs with randomized start time within the backup window. * Disabled — VMware Cloud Director organization members can create only jobs with no schedule assigned. | Yes | 1/1 |
| HighPriorityJob | Boolean | Defines whether the backup job has a high priority. Possible values:   * True * False | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <JobSettings>   <CustomSettings>true</CustomSettings>   <JobSchedulerType>Full</JobSchedulerType>     <HighPriorityJob>false</HighPriorityJob> </JobSettings> |

JSON Representation

|  |
| --- |
| "JobSettings": {   "CustomSettings": "true",   "JobSchedulerType": "Full",   "HighPriorityJob": false  } |

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

The example below updates the storage quota on the backup repository for the configuration with ID 228fef7b-6e5e-4107-886e-40c8f482b5c7.

|  |
| --- |
| Request:  PUT https://localhost:9398/api/vCloud/orgConfigs/228fef7b-6e5e-4107-886e-40c8f482b5c7    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <VCloudOrganizationConfig Href="https://localhost:9398/api/vCloud/orgConfigs/228fef7b-6e5e-4107-886e-40c8f482b5c7?format=Entity" Type="VCloudOrganizationConfig" Name="org02" UID="urn:veeam:VCloudOrganizationConfig:228fef7b-6e5e-4107-886e-40c8f482b5c7" xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">   <BackupServerUid>urn:veeam:BackupServer:1cf4ea89-89d9-4b4e-a285-71bd8c705222</BackupServerUid>   <RepositoryUid>urn:veeam:Repository:df9903aa-d2b6-4edd-9a0b-057bc8dd4451</RepositoryUid>   <QuotaGb>500</QuotaGb>   <IsDisabled>false</IsDisabled>   <JobSettings>     <DefaultSettings>true</DefaultSettings>     <JobSchedulerType>Full</JobSchedulerType>     <HighPriorityJob>false</HighPriorityJob>   </JobSettings>   <HostUid>urn:veeam:ManagedServer:24a14898-77d0-4881-bbf8-c8ba71ce4d55</HostUid>   <RepositoryFriendlyName>Repository 1</RepositoryFriendlyName> </VCloudOrganizationConfig>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>EditVCloudOrganizationConfig</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Href="https://localhost:9398/api/tasks/task-1" />     <Link Rel="Related" Type="VCloudOrganizationConfigReference" Href="https://localhost:9398/api/vCloud/orgConfigs/228fef7b-6e5e-4107-886e-40c8f482b5c7" Name="org02" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>EditVCloudOrganizationConfig</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |


