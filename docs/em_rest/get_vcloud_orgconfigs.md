---
title: "get_vcloud_orgconfigs"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_vcloud_orgconfigs.html"
last_updated: "8/15/2025"
product_version: "13.0.1.1071"
---


In this article

Returns a resource representation of a collection of VMware Cloud Director organization configurations.

|  |
| --- |
| Tip |
| To get a filtered and sorted collection of organization configurations, send the [GET /query?type=VCloudOrganizationConfig](get_query_vcloudorganizationconfig.md) request. |

Request

To get a list of VMware Cloud Director organization configurations, send the GET HTTP request to the /vCloud/orgConfigs resource.

|  |
| --- |
| Note |
| A list of configurations always contains a sample configuration with the name Other organizations. Settings specified for this configuration will be applied to all VMware Cloud Director organizations for which individual configurations are not created. |

HTTP Request

|  |
| --- |
| GET https://<Enterprise-Manager>:9398/api/vCloud/orgConfigs |

Request Header

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

In the response body, the REST API returns a representation of the /vCloud/orgConfigs resource.

Example 1

The example below returns an entity reference representation of a collection of VMware Cloud Director organization configurations.

|  |
| --- |
| Request:  GET https://localhost:9398/api/vCloud/orgConfigs    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |

Example 2

The example below returns an entity representation of a collection of VMware Cloud Director organization configurations.

|  |
| --- |
| Request:  GET https://localhost:9398/api/vCloud/orgConfigs?format=Entity    Request Header:  X-RestSvcSessionId   NDRjZmJkYmUtNWE5NS00MTU2LTg4NjctOTFmMDY5YjdjMmNj    Response:  200 OK    Response Body:  <VCloudOrganizationConfigs xmlns="http://www.veeam.com/ent/v1.0">   <VCloudOrganizationConfig Type="VCloudOrganizationConfig" Href="https://localhost:9398/api/vCloud/orgConfigs/7656b73b-52e3-48d8-a65c-a5850c0a8af9?format=Entity" Name="organization01" UID="urn:veeam:VCloudOrganizationConfig:7656b73b-52e3-48d8-a65c-a5850c0a8af9">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />       <Link Rel="Alternate" Type="VCloudOrganizationConfigReference" Href="https://localhost:9398/api/vCloud/orgConfigs/7656b73b-52e3-48d8-a65c-a5850c0a8af9" Name="organization01" />       <Link Rel="Edit" Type="VCloudOrganizationConfigReference" Href="https://localhost:9398/api/vCloud/orgConfigs/7656b73b-52e3-48d8-a65c-a5850c0a8af9" Name="organization01" />       <Link Rel="Delete" Href="https://localhost:9398/api/vCloud/orgConfigs/7656b73b-52e3-48d8-a65c-a5850c0a8af9" />       <Link Rel="Down" Type="VCloudOrganizationConfigBackupJobSettings" Href="https://localhost:9398/api/vCloud/orgConfigs/7656b73b-52e3-48d8-a65c-a5850c0a8af9/backupJobSettings" Name="organization01" />     </Links>     <BackupServerUid>urn:veeam:BackupServer:7445e6ce-86f5-4171-b909-dac209c66563</BackupServerUid>     <RepositoryUid>urn:veeam:Repository:425b6739-5082-4f7a-99fb-1ae13ef87d9f</RepositoryUid>     <QuotaGb>500</QuotaGb>     <IsDisabled>false</IsDisabled>     <JobSettings>       <DefaultSettings>false</DefaultSettings>       <JobSchedulerType>Full</JobSchedulerType>       <HighPriorityJob>true</HighPriorityJob>     </JobSettings>     <UsedQuotaMb>0</UsedQuotaMb>     <HostUid>urn:veeam:ManagedServer:24a14898-77d0-4881-bbf8-c8ba71ce4d55</HostUid>     <RepositoryFriendlyName>Repository 1</RepositoryFriendlyName>   </VCloudOrganizationConfig>   <VCloudOrganizationConfig Type="VCloudOrganizationConfig" Href="https://localhost:9398/api/vCloud/orgConfigs/c5ac3c79-5644-4064-b081-abc71dd2f370?format=Entity" Name="Other organizations" UID="urn:veeam:VCloudOrganizationConfig:c5ac3c79-5644-4064-b081-abc71dd2f370">     <Links>       <Link Rel="Up" Type="BackupServerReference" Href="https://localhost:9398/api/backupServers/7445e6ce-86f5-4171-b909-dac209c66563" Name="enterprise06.tech.local" />       <Link Rel="Alternate" Type="VCloudOrganizationConfigReference" Href="https://localhost:9398/api/vCloud/orgConfigs/c5ac3c79-5644-4064-b081-abc71dd2f370" Name="Other organizations" />       <Link Rel="Edit" Type="VCloudOrganizationConfigReference" Href="https://localhost:9398/api/vCloud/orgConfigs/c5ac3c79-5644-4064-b081-abc71dd2f370" Name="Other organizations" />       <Link Rel="Delete" Href="https://localhost:9398/api/vCloud/orgConfigs/c5ac3c79-5644-4064-b081-abc71dd2f370" />       <Link Rel="Down" Type="VCloudOrganizationConfigBackupJobSettings" Href="https://localhost:9398/api/vCloud/orgConfigs/c5ac3c79-5644-4064-b081-abc71dd2f370/backupJobSettings" Name="Other organizations" />     </Links>     <BackupServerUid>urn:veeam:BackupServer:7445e6ce-86f5-4171-b909-dac209c66563</BackupServerUid>     <RepositoryUid />     <QuotaGb>1024</QuotaGb>     <IsDisabled>true</IsDisabled>     <JobSettings>       <DefaultSettings>true</DefaultSettings>       <JobSchedulerType>Full</JobSchedulerType>       <HighPriorityJob>false</HighPriorityJob>     </JobSettings>     <UsedQuotaMb>0</UsedQuotaMb>     <HostUid>urn:veeam:ManagedServer:00000000-0000-0000-0000-000000000000</HostUid>     <RepositoryFriendlyName>N/A</RepositoryFriendlyName>   </VCloudOrganizationConfig> </VCloudOrganizationConfigs> </VCloudOrganizationConfigs> |

Page updated 8/15/2025

Page content applies to build 13.0.1.1071
