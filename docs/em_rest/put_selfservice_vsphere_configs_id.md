---
title: "PUT /selfService/vSphere/Configs/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/put_selfservice_vsphere_configs_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# PUT /selfService/vSphere/Configs/{ID}


Edits settings of a tenant access configuration with the specified ID.

Request

To edit settings of the tenant access configuration, send the PUT HTTP request to the /selfService/vSphere/Configs/{ID} resource.

HTTP Request

|  |
| --- |
| PUT https://<Enterprise-Manager>:9398/api/selfService/vSphere/Configs/{ID} |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Content-Type | True | Identifies the format of the request body message. Possible values:   * application/xml * application/json |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

In the request body, the client must send parameters for the tenant access configuration whose settings must be updated. The body of the request must conform to the [XML Schema Definition](em_web_api_specifications.md) of Veeam Backup Enterprise Manager REST API.

|  |
| --- |
| Important |
| If you use the XML media type, make sure that the order of parameters in the request body is correct. For details, see request body examples in this section. |

The request body must contain the following elements:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| BackupServerUid | UidType | UID of the backup server that must process VMs available to the tenant of the vSphere Self-Service Backup Portal, for example: urn:veeam:BackupServer:1cf4ea89-89d9-4b4e-a285-71bd8c705222. | False | 1/1 |
| RepositoryUid | UidType | UID of the backup repository on which the storage quota for the tenant of the portal must be created, for example: urn:veeam:Repository:82db96c3-445c-4a7e-9587-f2d523e839f4. | Yes | 1/1 |
| QuotaGb | Long | Size of the storage quota assigned to the tenant (in GB). | Yes | 1/1 |
| PerUser | Boolean | Defines whether users of the group for which the tenant access configuration is created will have separate quotas on the backup repository and what backup jobs will be available to users. Possible values:   * True — each user of the group has a separate quota on the backup repository. Each user has access to backup jobs created by this user only. * False — all users of the group share the same quota on the backup repository. Each user has access to all backup jobs created by users of the group. | Yes | 0/1 |
| Account | VSphereSelfServiceConfigAccountInfoType | Specifies the tenant access configuration settings. For details, see [vSphere Self-Service Account Settings](#account) | False | 1/1 |
| JobSettings | VSphereSelfServiceConfigEntityTypeJobSettings | vSphere backup job options set for the organization. For details, see [vSphere Self-Service Backup Job Settings](#job). | Yes | 1/1 |
| VCentersScope | VCentersScopeListType | Defines a list of vCenter Servers whose VMs are available to the tenant. By default, the tenant has access to all vCenter Servers. For details, see [vCenters Scope Settings](#vCenters). | Yes | 0/1 |
| Tags | TagsListType | vSphere tags that define what VMs are available to the tenant. For details, see [vSphere Tags](#tags). | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

JSON Representation

|  |
| --- |
| {   "BackupServerUid": "urn:veeam:BackupServer:7445e6ce-86f5-4171-b909-dac209c66563",   "RepositoryUid": "urn:veeam:Repository:425b6739-5082-4f7a-99fb-1ae13ef87d9f",   "QuotaGb": 500,   "PerUser": false,   "Account": {    "AccountName": "Administrators",    "AccountSid": "S-1-5-32-544",    "AccountType": "Group"   },   "JobSettings": {    "DefaultSettings": false,    "JobSchedulerType": "Full",    "HighPriorityJob": true,    "TemplateJobUid": null   },   "VCentersScopes": [    "urn:veeam:ManagedServer:6edb23da-560b-4759-951f-1da6aca08169",    "urn:veeam:ManagedServer:095585e0-6a9a-4bb8-8433-a1d815687ce9"   ],   "Tags": [    "RestAPITag"   ],   "UsedQuotaMb": 0,   "Name": "Administrators",   "UID": "urn:veeam:VSphereSelfServiceConfig:c6a041d0-36a1-47c7-9f4b-a12327796c68",   "Links": null,   "Href": "https://localhost:9398/api/selfService/vSphere/Configs/c6a041d0-36a1-47c7-9f4b-a12327796c68?format=Entity",   "Type": "VSphereSelfServiceConfig"  } |

vSphere Self-Service Backup Job Settings

You can define the following parameters for tenant backup jobs:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| DefaultSettings | Boolean | Defines what settings are applied to backup jobs created by the tenant of vSphere Self-Service Backup Portal. Possible values:   * True — tenant jobs are configured with the default settings of a backup job for vSphere VMs. * False — tenant jobs are configured with settings of the backup job specified as a template. | Yes | 0/1 |
| JobSchedulerType | String | Job scheduling options. Possible values:   * Full — tenant of the vSphere Self-Service Backup Portal has full access to all job scheduling options. * Partial — tenant of the vSphere Self-Service Backup Portal can create daily and monthly jobs only. * Random — tenant of the vSphere Self-Service Backup Portal can create daily jobs with randomized start time within the backup window. * Disabled — tenant of the vSphere Self-Service Backup Portal can create only jobs with no schedule assigned. | Yes | 0/1 |
| HighPriorityJob | Boolean | Defines whether the backup job has a high priority. Possible values:   * True * False | Yes | 0/1 |

For example:

XML Representation

|  |
| --- |
| <JobSettings>   <DefaultSettings>true</DefaultSettings>   <JobSchedulerType>Full</JobSchedulerType>   <HighPriorityJob>true</HighPriorityJob> </JobSettings> |

JSON Representation

|  |
| --- |
| "JobSettings": {   "DefaultSettings": true,   "JobSchedulerType": "Full"   "HighPriorityJob": true  } |

vSphere Self-Service Account Settings

You must specify the following parameters of the edited tenant access configuration:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| AccountName | String | Name of the tenant access configuration. | False | 1/1 |
| AccountSid | String | ID of the tenant access configuration, for example: S-1-5-21-2710250414-1144789048-1111555807-25028. | False | 0/1 |
| AccountType | String | Type of the tenant access configuration. Possible values:   * User — tenant access configuration is created for a vSphere user. * Group — tenant access configuration is created for a vSphere group. | False | 1/1 |

For example:

XML Representation

|  |
| --- |
| <Account>   <AccountName>Domain Users</AccountName>   <AccountSid>S-1-5-21-2710250414-1144789048-1111555807-513</AccountSid>   <AccountType>Group</AccountType> </Account> |

JSON Representation

|  |
| --- |
| "Account": {   "AccountName": "Domain Users",   "AccountSid": "S-1-5-21-2710250414-1144789048-1111555807-513",   "AccountType": "Group"  } |

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

You can define the following parameters for vSphere tags:

| Element | Type | Description | Modifiable | Min/Max Occurrence |
| --- | --- | --- | --- | --- |
| Tag | String | vSphere tag assigned to a VM that must be available to the tenant.  You must specify tags in the tenant access configuration if the vSphere tags delegation mode is selected in Veeam Backup Enterprise Manager. The tenant will be able to back up only those VMs to which the specified tags are assigned. | Yes | 0/- |

For example:

XML Representation

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

The example below updates the storage quota on the backup repository for the configuration with ID 21774252-e680-49ce-9f99-6764a8b84440.

|  |
| --- |
| Request:  PUT https://localhost:9398/api/vCloud/orgConfigs/21774252-e680-49ce-9f99-6764a8b84440    Request Headers:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj Content-Type         application/xml    Request Body:  <?xml version="1.0" encoding="utf-8"?> <VSphereSelfServiceConfig xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" Href="https://localhost:9398/api/selfService/vSphere/Configs/c6a041d0-36a1-47c7-9f4b-a12327796c68?format=Entity" Type="VSphereSelfServiceConfig" Name="Administrators" UID="urn:veeam:VSphereSelfServiceConfig:c6a041d0-36a1-47c7-9f4b-a12327796c68" xmlns="http://www.veeam.com/ent/v1.0">   <BackupServerUid>urn:veeam:BackupServer:7445e6ce-86f5-4171-b909-dac209c66563</BackupServerUid>   <RepositoryUid>urn:veeam:Repository:425b6739-5082-4f7a-99fb-1ae13ef87d9f</RepositoryUid>   <QuotaGb>500</QuotaGb>   <PerUser>false</PerUser>   <Account>     <AccountName>Administrators</AccountName>     <AccountSid>S-1-5-32-544</AccountSid>     <AccountType>Group</AccountType>   </Account>   <JobSettings>     <DefaultSettings>false</DefaultSettings>     <JobSchedulerType>Full</JobSchedulerType>     <HighPriorityJob>true</HighPriorityJob>   </JobSettings>   <VCentersScope>     <VCenterUid>urn:veeam:ManagedServer:6edb23da-560b-4759-951f-1da6aca08169</VCenterUid>     <VCenterUid>urn:veeam:ManagedServer:095585e0-6a9a-4bb8-8433-a1d815687ce9</VCenterUid>   </VCentersScope>   <Tags>     <Tag>RestAPITag</Tag>   </Tags>   <UsedQuotaMb>0</UsedQuotaMb> </VSphereSelfServiceConfig>    Response:  202 Accepted    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Type="Task" Href="https://localhost:9398/api/tasks/task-1" />   </Links>   <TaskId>task-1</TaskId>   <State>Running</State>   <Operation>EditVSphereOrganizationConfig</Operation> </Task> |

To track the status of the operation, send the GET HTTP request to the received task resource:

|  |
| --- |
| Request:  GET https://localhost:9398/api/tasks/task-1    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <Task xmlns="http://www.veeam.com/ent/v1.0" Type="Task" Href="https://localhost:9398/api/tasks/task-1">   <Links>     <Link Rel="Delete" Href="https://localhost:9398/api/tasks/task-1" />     <Link Rel="Related" Type="VSphereOrganizationConfigReference" Href="https://localhost:9398/api/vCloud/orgConfigs/228fef7b-6e5e-4107-886e-40c8f482b5c7" Name="org02" />   </Links>   <TaskId>task-1</TaskId>   <State>Finished</State>   <Operation>EditVSphereOrganizationConfig</Operation>   <Result Success="true">     <Message>Ok</Message>   </Result> </Task> |


