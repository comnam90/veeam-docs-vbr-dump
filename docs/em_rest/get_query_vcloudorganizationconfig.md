---
title: "GET /query?type=VCloudOrganizationConfig"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_query_vcloudorganizationconfig.html"
last_updated: "2026"
product_version: "13.1.0.411"
---

# GET /query?type=VCloudOrganizationConfig


Returns a resource representation of a collection of VMware Cloud Director organization configurations. For details, see [/vCloud/orgConfigs](vcloud_orgconfigs.md).

Request

To get a list of VMware Cloud Director organization configurations, send the GET HTTP request to the query with the type parameter set to VCloudOrganizationConfig.

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/query?type=VCloudOrganizationConfig |

Request Headers

The request contains the following headers:

Request Headers

| Header | Required | Description |
| X-RestSvcSessionId | True | The request requires authorization. In the header, the client must send a session ID copied from the server reply to the request creating a new logon session. For details, see [Authentication and Security](authentication_and_security.md). |
| Accept | False | Identifies the format of the response. Possible values:   * application/xml — the client can send this value in the header to accept response in the XML format. * application/json — the client must send this value in the header to accept the request in the JSON format.   If the request does not contain the header, the server will return the response in the XML format. |

Request Body

None.

Optional Parameters

In the query, you can use the following parameters for filtering and sorting.

Optional Parameters

| Parameter | Type | Description |
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

Response Headers

| Header | Description |
| Content-length | The length of the response body. |
| Content-type | The media type and syntax of the request body message. Possible values:   * application/xml * application/json |

Response Body

In the response body, the REST API returns a representation of the /vCloud/orgConfigs resource collection.

Example

The example below returns an entity resource representation of a collection of enabled vCD organization configurations created on the enterprise06.tech.local backup server.

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=VCloudOrganizationConfig&format=Entities&filter=BackupServerName=="enterprise06.tech.local";Disabled==false  Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj  Response:  200 OK  Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0">   <Entities>     <VCloudOrganizationConfigs>       <VCloudOrganizationConfig Type="VCloudOrganizationConfig" Href="https://localhost:9398/api/vCloud/orgConfigs/21e1e4bb-1adc-4851-bc3a-5d25bb39ff10?format=Entity" Name="organization02" UID="urn:veeam:VCloudOrganizationConfig:21e1e4bb-1adc-4851-bc3a-5d25bb39ff10">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Alternate" Type="VCloudOrganizationConfigReference" Href="https://localhost:9398/api/vCloud/orgConfigs/21e1e4bb-1adc-4851-bc3a-5d25bb39ff10" Name="organization02" />           <Link Rel="Edit" Type="VCloudOrganizationConfigReference" Href="https://localhost:9398/api/vCloud/orgConfigs/21e1e4bb-1adc-4851-bc3a-5d25bb39ff10" Name="organization02" />           <Link Rel="Delete" Href="https://localhost:9398/api/vCloud/orgConfigs/21e1e4bb-1adc-4851-bc3a-5d25bb39ff10" />           <Link Rel="Down" Type="VCloudOrganizationConfigBackupJobSettings" Href="https://localhost:9398/api/vCloud/orgConfigs/21e1e4bb-1adc-4851-bc3a-5d25bb39ff10/backupJobSettings" Name="organization02" />         </Links>         <BackupServerUid>urn:veeam:BackupServer:7445e6ce-86f5-4171-b909-dac209c66563</BackupServerUid>         <RepositoryUid>urn:veeam:Repository:425b6739-5082-4f7a-99fb-1ae13ef87d9f</RepositoryUid>         <QuotaGb>100</QuotaGb>         <IsDisabled>false</IsDisabled>         <JobSettings>           <DefaultSettings>false</DefaultSettings>           <JobSchedulerType>Full</JobSchedulerType>           <HighPriorityJob>false</HighPriorityJob>         </JobSettings>         <UsedQuotaMb>0</UsedQuotaMb>         <HostUid>urn:veeam:ManagedServer:24a14898-77d0-4881-bbf8-c8ba71ce4d55</HostUid>         <RepositoryFriendlyName>Repository 1</RepositoryFriendlyName>       </VCloudOrganizationConfig>       <VCloudOrganizationConfig Type="VCloudOrganizationConfig" Href="https://localhost:9398/api/vCloud/orgConfigs/7656b73b-52e3-48d8-a65c-a5850c0a8af9?format=Entity" Name="organization01" UID="urn:veeam:VCloudOrganizationConfig:7656b73b-52e3-48d8-a65c-a5850c0a8af9">         <Links>           <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />           <Link Rel="Alternate" Type="VCloudOrganizationConfigReference" Href="https://localhost:9398/api/vCloud/orgConfigs/7656b73b-52e3-48d8-a65c-a5850c0a8af9" Name="organization01" />           <Link Rel="Edit" Type="VCloudOrganizationConfigReference" Href="https://localhost:9398/api/vCloud/orgConfigs/7656b73b-52e3-48d8-a65c-a5850c0a8af9" Name="organization01" />           <Link Rel="Delete" Href="https://localhost:9398/api/vCloud/orgConfigs/7656b73b-52e3-48d8-a65c-a5850c0a8af9" />           <Link Rel="Down" Type="VCloudOrganizationConfigBackupJobSettings" Href="https://localhost:9398/api/vCloud/orgConfigs/7656b73b-52e3-48d8-a65c-a5850c0a8af9/backupJobSettings" Name="organization01" />         </Links>         <BackupServerUid>urn:veeam:BackupServer:7445e6ce-86f5-4171-b909-dac209c66563</BackupServerUid>         <RepositoryUid>urn:veeam:Repository:425b6739-5082-4f7a-99fb-1ae13ef87d9f</RepositoryUid>         <QuotaGb>600</QuotaGb>         <IsDisabled>false</IsDisabled>         <JobSettings>           <DefaultSettings>false</DefaultSettings>           <JobSchedulerType>Full</JobSchedulerType>           <HighPriorityJob>true</HighPriorityJob>         </JobSettings>         <UsedQuotaMb>0</UsedQuotaMb>         <HostUid>urn:veeam:ManagedServer:24a14898-77d0-4881-bbf8-c8ba71ce4d55</HostUid>         <RepositoryFriendlyName>Repository 1</RepositoryFriendlyName>       </VCloudOrganizationConfig>     </VCloudOrganizationConfigs>   </Entities>   <PagingInfo PagesCount="1" PageSize="100" PageNum="1">     <Links>       <Link Rel="First" Href="https://localhost:9398/api/query?type=VCloudOrganizationConfig&format=Entities&filter=BackupServerName=="enterprise06.tech.local";Disabled==false&pageSize=100&page=1" />       <Link Rel="Last" Href="https://localhost:9398/api/query?type=VCloudOrganizationConfig&format=Entities&filter=BackupServerName=="enterprise06.tech.local";Disabled==false&pageSize=100&page=1" />     </Links>   </PagingInfo> </QueryResult> |

Page updated 2026-07-29

