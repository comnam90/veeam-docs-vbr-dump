---
title: "GET /query?type=VsphereSelfServiceConfig"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_vsphereselfserviceconfig.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# GET /query?type=VsphereSelfServiceConfig


Returns a resource representation of a collection of vSphere Self-Service Backup Portal tenant access configurations. For details, see [/selfService/vSphere/Configs](selfservice_vsphere_configs.md).

Request

To get a list of vSphere Self-Service Backup Portal tenant access configurations, send the GET HTTP request to the query with the type parameter set to VsphereSelfServiceConfig.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=VsphereSelfServiceConfig |

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
| UID | UidType | UID of the tenant access configuration resource. |
| Name | String | Name of the tenant access configuration, for example: tech\william.fox. |
| BackupServerUid | UidType | UID of the backup server parent to the access configuration resource, for example: urn:veeam:BackupServer:0874ab95-10e5-4f25-84df-2782ad81f3e5. |
| BackupServerName | String | Name of the backup server parent to the access configuration resource. |
| JobSchedulerType | String | Job scheduling options. Possible values:   * Full — tenant of the vSphere Self-Service Backup Portal has full access to all job scheduling options. * Partial — tenant of the vSphere Self-Service Backup Portal can create daily and monthly jobs only. * Random — tenant of the vSphere Self-Service Backup Portal can create daily jobs with randomized start time within the backup window. * Disabled — tenant of the vSphere Self-Service Backup Portal can create only jobs with no schedule assigned. |
| AccountType | String | Type of the vSphere Self-Service Backup Portal tenant account. Possible values:   * User — tenant account is a user account. * Group — tenant account is a group account. |
| PerUser | Boolean | Defines whether users of the group for which the tenant access configuration is created will have separate quotas on the backup repository and what backup jobs will be available to users. Possible values:   * True — each user of the group has a separate quota on the backup repository. Each user has access to backup jobs created by this user only. * False — all users of the group share the same quota on the backup repository. Each user has access to all backup jobs created by users of the group. |
| QuotaGb | Long | Size of the storage quota assigned to the tenant (in GB). |
| RepositoryUid | UidType | UID of the backup repository on which the storage quota for the tenant is created, for example: urn:veeam:Repository:82db96c3-445c-4a7e-9587-f2d523e839f4. |
| UsedQuota | Long | Amount of space on the storage quota consumed by the tenant (in MB). |

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

In the response body, the REST API returns a representation of the /selfService/vSphere/Configs resource collection.

Example

The example below returns an entity resource representation of a collection of vSphere Self-Service Backup Portal tenant access configurations created for Group accounts on the enterprise06.tech.local backup server. The results are ordered in the acceding order by the Name parameter.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=VSphereSelfServiceConfig&format=Entities&sortAsc=Name&filter=BackupServerName=="enterprise06.tech.local";AccountType==Group    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |


