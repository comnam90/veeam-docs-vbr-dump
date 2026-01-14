---
title: "get_query_vcloudorganizationconfig"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_vcloudorganizationconfig.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a collection of VMware Cloud Director organization configurations. For details, see [/vCloud/orgConfigs](vcloud_orgconfigs.md).

Request

To get a list of VMware Cloud Director organization configurations, send the GET HTTP request to the query with the type parameter set to VCloudOrganizationConfig.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=VCloudOrganizationConfig |

Request Headers

The request contains the following headers:

| Header | Required | Description |
| --- | --- | --- |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Optional Parameters

In the query, you can use the following parameters for filtering and sorting.

| Parameter | Type | Description |
| --- | --- | --- |
| UID | UidType | UID of the VMware Cloud Director organization configuration resource, for example: urn:veeam:BackupFile:0874ab95-10e5-4f25-84df-2782ad81f3e5. |
| Name | String | Name of the VMware Cloud Director organization configuration resource, for example: org1. |
| RepositoryUid | UidType | UID of the backup repository on which the storage quota for the VMware Cloud Director organization is created, for example: urn:veeam:Repository:82db96c3-445c-4a7e-9587-f2d523e839f4. |
| QuotaGb | Long | Size of the storage quota assigned to the VMware Cloud Director organization (in GB). |
| Disabled | Boolean | Defines if the default VMware Cloud Director organization configuration is in the disabled or enabled state. Possible values:   * True — the default configuration is disabled. Self-service backup is unavailable for VMware Cloud Director organizations that do not have individual configurations. * False — the default configuration is enabled. VMware Cloud Director organizations for which individual configurations were not created can perform self-service backup. |
| JobSchedulerType | String | Job scheduling options. Possible values:   * Full — VMware Cloud Director organization members have full access to all job scheduling options. * Partial — VMware Cloud Director organization members can create daily and monthly jobs only. * Random — VMware Cloud Director organization members can create daily jobs with randomized start time within the backup window. * Disabled — VMware Cloud Director organization members can create only jobs with no schedule assigned. |
| UsedQuota | Long | Amount of space on the storage quota consumed by the VMware Cloud Director organization (in MB). |
| BackupServerUid | UidType | UID of the backup server parent to the VMware Cloud Director organization configuration resource. |
| BackupServerName | String | Name of the backup server parent to the VMware Cloud Director organization configuration resource. |
| HostUid | UidType | UID of the VMware Cloud Director host where the VMware Cloud Director organization has been created. |
| RepositoryFriendlyName | String | Backup repository name displayed to VMware Cloud Director organization members, for example: Backup Repository 1. |

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

In the response body, the REST API returns a representation of the /vCloud/orgConfigs resource collection.

Example

The example below returns an entity resource representation of a collection of enabled vCD organization configurations created on the enterprise06.tech.local backup server.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=VCloudOrganizationConfig&format=Entities&filter=BackupServerName=="enterprise06.tech.local";Disabled==false    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
