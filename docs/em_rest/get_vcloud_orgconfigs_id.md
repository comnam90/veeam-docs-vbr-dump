---
title: "GET /vCloud/orgConfigs/{ID}"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_vcloud_orgconfigs_id.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---

# GET /vCloud/orgConfigs/{ID}


Returns a resource representation of a VMware Cloud Director organization configuration with the specified ID.

Request

To get a resource representation of the VMware Cloud Director organization configuration, send the GET HTTP request to the /vCloud/orgConfigs/{ID} resource:

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/vCloud/orgConfigs/{ID} |

or

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/vCloud/orgConfigs/{ID}?format=Entity |

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

In the response body, the REST API returns an entity or an entity reference of the /vCloud/orgConfigs/{ID} resource. The resource entity contains the following parameters and links.

Parameters

| Element | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the VMware Cloud Director organization configuration resource, for example: urn:veeam:BackupFile:0874ab95-10e5-4f25-84df-2782ad81f3e5. |
| Name | String | Name of the VMware Cloud Director organization configuration resource, for example: org1. |
| BackupServerUid | UidType | UID of the backup server parent to the VMware Cloud Director organization configuration resource. |
| RepositoryUid | UidType | UID of the backup repository on which the storage quota for the VMware Cloud Director organization is created, for example: urn:veeam:Repository:82db96c3-445c-4a7e-9587-f2d523e839f4. |
| QuotaGb | Long | Size of the storage quota assigned to the VMware Cloud Director organization (in GB). |
| IsDisabled | Boolean | Defines if the default VMware Cloud Director organization configuration is in the disabled or enabled state. Possible values:   * True — the default configuration is disabled. Self-service backup is unavailable for VMware Cloud Director organizations that do not have individual configurations. * False — the default configuration is enabled. VMware Cloud Director organizations for which individual configurations were not created can perform self-service backup. |
| JobSettings | — | Job settings used for the organization configuration. For details, see [Job Settings](#jobsettings). |
| UsedQuotaMb | Long | Amount of space on the storage quota consumed by the VMware Cloud Director organization (in MB). |
| HostUid | UidType | UID of the VMware Cloud Director host where the VMware Cloud Director organization has been created. |
| RepositoryFriendlyName | String | Backup repository name displayed to VMware Cloud Director organization members, for example: Backup Repository 1. |

To view query parameters that you can use for filtering or sorting, see [GET /query?type=VCloudOrganizationConfig](get_query_vcloudorganizationconfig.md).

Job Settings

The JobSettings element contains the following job settings.

| Element | Type | Description |
| --- | --- | --- |
| DefaultSettings | Boolean | Defines if the default VMware Cloud Director organization configuration is in the disabled or enabled state. Possible values:   * True — the default configuration is disabled. Self-service backup is unavailable for VMware Cloud Director organizations that do not have individual configurations. * False — the default configuration is enabled. VMware Cloud Director organizations for which individual configurations were not created can perform self-service backup. |
| JobSchedulerType | String | Job scheduling options. Possible values:   * Full — VMware Cloud Director organization members have full access to all job scheduling options. * Partial — VMware Cloud Director organization members can create daily and monthly jobs only. * Random — VMware Cloud Director organization members can create daily jobs with randomized start time within the backup window. * Disabled — VMware Cloud Director organization members can create only jobs with no schedule assigned. |
| HighPriorityJob | Boolean | Defines whether the backup job has a high priority. Possible values:   * True * False |
| TemplateJobUid | UidType | UID of the VMware Cloud Director backup job that will be used as a template for VMware Cloud Director organization VMs processing. The backup job must be created in advance on the backup server connected to Veeam Backup Enterprise Manager.  Settings of the specified job will be applied to backup jobs created by tenant-side users. If the job UID is not specified, tenant-side jobs will be configured with the default VMware Cloud Director backup job settings.  Job settings applied to backup jobs for the VMware Cloud Director organization will be listed in the representation of the [/vCloud/orgConfigs/{ID}/backupJobSettings](vcloud_orgconfigs_id_backupjobsettings.md) resource. |

Links

| Reference | Relationship | Description |
| --- | --- | --- |
| /backupServers/{ID} | Up | URL of the [/backupServers/{ID}](backupservers_id.md) resource — a backup server that contains the VMware Cloud Director server in its infrastructure. |
| /vCloud/orgConfigs/{ID} | Alternate | Alternate URL of the [/vCloud/orgConfigs/{ID}](vcloud_orgconfigs_id.md) resource. |
| /vCloud/orgConfigs/{ID} | Edit | URL for the [PUT /vCloud/orgConfigs/{ID}](put_vcloud_orgconfigs_id.md) request. |
| /vCloud/orgConfigs/{ID} | Delete | URL for the [DELETE /vCloud/orgConfigs/{ID}](delete_vcloud_orgconfigs_id.md) request. |
| /vCloud/orgConfigs/{ID}/backupJobSettings | Down | URL of the [/vCloud/orgConfigs/{ID}/backupJobSettings](vcloud_orgconfigs_id_backupjobsettings.md) resource — job settings applied to backup jobs for the VMware Cloud Director organization. |

Example

The example below returns an entity representation of the configuration with ID ee1018b4-6f52-489e-80b7-8005e0b2d640.

|  |
| --- |
| Request:  GET https://localhost:9398/api/vCloud/orgConfigs/ee1018b4-6f52-489e-80b7-8005e0b2d640?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <VCloudOrganizationConfig xmlns="http://www.veeam.com/ent/v1.0" Type="VCloudOrganizationConfig" Href="https://localhost:9398/api/vCloud/orgConfigs/ee1018b4-6f52-489e-80b7-8005e0b2d640?format=Entity" Name="org1" UID="urn:veeam:VCloudOrganizationConfig:ee1018b4-6f52-489e-80b7-8005e0b2d640"> |


