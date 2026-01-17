---
title: "GET /selfService/vSphere/Configs/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_selfservice_vsphere_configs_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# GET /selfService/vSphere/Configs/{ID}


Returns a resource representation of a vSphere Self-Service Backup Portal tenant access configuration with the specified ID.

Request

To get a resource representation of the vSphere Self-Service Backup Portal tenant access configuration, send the GET HTTP request to the /selfService/vSphere/Configs/{ID} resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/selfService/vSphere/Configs/{ID} |

or

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/selfService/vSphere/Configs/{ID}?format=Entity |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Response

The server returns the following response to the client.

Response Codes

A successfully completed operation returns response code 200 OK.

Response Headers

The response to this request contains the following headers. The response may also include additional standard HTTP headers.

| Header | Description |
| --- | --- |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns an entity or an entity reference of the /selfService/vSphere/Configs/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the tenant access configuration resource. |
| Name | String | Name of the tenant access configuration, for example: tech\william.fox. |
| BackupServerUid | UidType | UID of the backup server parent to the access configuration resource, for example: urn:veeam:BackupServer:0874ab95-10e5-4f25-84df-2782ad81f3e5. |
| RepositoryUid | UidType | UID of the backup repository on which the storage quota for the tenant is created, for example: urn:veeam:Repository:82db96c3-445c-4a7e-9587-f2d523e839f4. |
| QuotaGb | Long | Size of the storage quota assigned to the tenant (in GB). |
| PerUser | Boolean | Defines whether users of the group for which the tenant access configuration is created will have separate quotas on the backup repository and what backup jobs will be available to users. Possible values:   * True — each user of the group has a separate quota on the backup repository. Each user has access to backup jobs created by this user only. * False — all users of the group share the same quota on the backup repository. Each user has access to all backup jobs created by users of the group. |
| Account | VSphereSelfServiceConfigAccountInfoType | Tenant access configuration settings. For details, see [vSphere Self-Service Account Settings](#account) |
| JobSettings | — | vSphere backup job options set for the organization. For details, see [vSphere Self-Service Backup Job Settings](#job). |
| VCentersScope | VCentersScopeListType | List of vCenter Servers whose VMs are available to the tenant. By default, the tenant has access to all vCenter Servers. For details, see [vCenters Scope Settings](#vCenters). |
| Tags | TagsListType | vSphere tags that define what VMs are available to the tenant. For details, see [vSphere Tags](#tags). |
| UsedQuota | Long | Amount of space on the storage quota consumed by the tenant (in MB). |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=VsphereSelfServiceConfig](get_query_vsphereselfserviceconfig.md).

vSphere Self-Service Account Settings

The Account element contains the following tenant access configuration settings.

| Element | Type | Description |
| --- | --- | --- |
| AccountName | String | Name of the tenant access configuration. |
| AccountSid | String | ID of the tenant access configuration, for example: S-1-5-21-2710250414-1144789048-1111555807-25028. |
| AccountType | String | Type of the tenant access configuration. Possible values:   * User — tenant access configuration is created for a vSphere user. * Group — tenant access configuration is created for a vSphere group. |

vSphere Self-Service Backup Job Settings

The JobSettings element contains the following backup job settings.

| Element | Type | Description |
| --- | --- | --- |
| DefaultSettings | Boolean | Defines what settings are applied to backup jobs created by the tenant of vSphere Self-Service Backup Portal. Possible values:   * True — tenant jobs are configured with the default settings of a backup job for vSphere VMs. * False — tenant jobs are configured with settings of the backup job specified as a template. |
| JobSchedulerType | String | Job scheduling options. Possible values:   * Full — tenant of the vSphere Self-Service Backup Portal has full access to all job scheduling options. * Partial — tenant of the vSphere Self-Service Backup Portal can create daily and monthly jobs only. * Random — tenant of the vSphere Self-Service Backup Portal can create daily jobs with randomized start time within the backup window. * Disabled — tenant of the vSphere Self-Service Backup Portal can create only jobs with no schedule assigned. |
| HighPriorityJob | Boolean | Defines whether the backup job has a high priority. Possible values:   * True * False |

vCenters Scope Settings

The VCentersScope element contains the following vCenters Scope settings.

| Element | Type | Description |
| --- | --- | --- |
| VCenterUid | UidType | UID of the vCenter Server  that must be available to the tenant, for example: urn:veeam:ManagedServer:6edb23da-560b-4759-951f-1da6aca08169. |

vSphere Tags

The Tags element contains a list of Tag elements.

| Element | Type | Description |
| --- | --- | --- |
| Tag | String | vSphere tag assigned to a VM that must be available to the tenant.  If tags are specified in the tenant access configuration, the vSphere tags delegation mode is selected in Veeam Backup Enterprise Manager. The tenant is able to back up only those VMs to which the specified tags are assigned. |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server that contains the VMware Cloud Director server in its infrastructure. |
| /vCloud/orgConfigs/{ID} | Alternate | Alternate URL of the [/vCloud/orgConfigs/{ID}](vcloud_orgconfigs_id.md) resource. |
| /vCloud/orgConfigs/{ID} | Edit | URL for the [PUT /vCloud/orgConfigs/{ID}](put_vcloud_orgconfigs_id.md) request. |
| /vCloud/orgConfigs/{ID} | Delete | URL for the [DELETE /vCloud/orgConfigs/{ID}](delete_vcloud_orgconfigs_id.md) request. |
| /vCloud/orgConfigs/{ID}/backupJobSettings | Down | URL of the [/vCloud/orgConfigs/{ID}/backupJobSettings](vcloud_orgconfigs_id_backupjobsettings.md) resource — job settings applied to backup jobs for the VMware Cloud Director organization. |

Example

The example below returns an entity representation of the configuration with ID c6a041d0-36a1-47c7-9f4b-a12327796c68.

|  |
| --- |
| Request:  GET https://localhost:9398/api/selfService/vSphere/Configs/c6a041d0-36a1-47c7-9f4b-a12327796c68?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <VSphereSelfServiceConfig xmlns="http://www.veeam.com/ent/v1.0" Type="VSphereSelfServiceConfig" Href="https://localhost:9398/api/selfService/vSphere/Configs/c6a041d0-36a1-47c7-9f4b-a12327796c68?format=Entity" Name="Administrators" UID="urn:veeam:VSphereSelfServiceConfig:c6a041d0-36a1-47c7-9f4b-a12327796c68"> |


